# vm-gpu-passthrough-spice

Keywords: spice, vioserial, looking glass, DXGI, inter-vm shared memory

# Objective
Creating a GPU Passthrough Virtual "Video" Adapter GPUPT to forward GPU Accelerated VM Client Screen, like my lagecy Windows XP, to host "Display Spice", via standard Spice protocol.

The basic idea is to capture & stream the video frame buffer of the GPU and forward it via Spice protocol

# Why?

# Is it possible?  
There are numerous technical issues and uncertainties that need divide and conquer, like 
1) the most efficient way to access a physical GPU frame buffer in Windows, frame buffer capture via front buffer or back buffer?
- GetFrontBufferData()
3) a socket server that capture the frame buffer and forward it as a remote client
4) before entering the guest OS and loading the virtual driver, what to display? Like a dummy booting screen?
5) after entering the guest OS, switched to the socket server?
6) How about the listen type and TLS in the Display Spice?
7) What's the bandwidth required to display one standard HD 1920x1080 x 24-bit x 60Hz (= 374MB/s) display?  How about dual 8k x 24-bit x 120Hz (= 23.888 GB/s)?
8) Adding it to qemu and virt-manager/libvirt?
9) Implementing it as a Windows driver?  Reference to VGA and QXL driver?
10) Fully integrated to virt-manager on libvirt on qemu KVM and can be used on cockpit
11) Windows XP doesn't support DXGI desktop duplication...


References
1) https://www.spice-space.org/spice-user-manual.html#guest-additions
2) https://forum.level1techs.com/t/windows-over-spice-with-gpu-passtrough/145791/8
3) https://www.youtube.com/watch?v=U44lihtNVVM  (how looking glass use)
