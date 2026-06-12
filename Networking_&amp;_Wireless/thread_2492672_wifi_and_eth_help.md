---
title: "wifi and eth help"
date: 2023-11-19
forum: Networking &amp; Wireless
---

### Post by frozone1445 on 2023-11-19
i have been struggling trying to setup my wifi adapater to my V.M and have been doing research and found out alot of problems im running into are because of the vm im using i now have a laptop with ubuntu on it but im wondering im using a rtl8187 wireless and im learning so please forgive me if this is a very beginner question but do i keep my eth cord in and run my wireless adapter or do i have to connect from my wireless adapter and do everything from there? thank you in advance

---

### Post by TheFu on 2023-11-19
VMs don't use real hardware. They only use virtual hardware, so as long as the host OS is accessing the network device you want, then you can setup a bridge on it and the VM should be connected to that named bridge in the VM settings (you need to do that). Use the virtio network driver.  Then treat it like any other wired connection inside the VM.

Not all wireless adapters support bridging, so it isn't recommended. Always use wired ethernet on the host OS instead - also it is best to setup static IPs on both the VM and the hostOS, unless your VM will just be a play desktop and using NAT.

Without the specific, exact hypervisor being used, nobody can provide detail steps. Those are general answers.

Only use 1 network connection at a time, if you are new to Linux.  Disable the one you aren't using.

---

