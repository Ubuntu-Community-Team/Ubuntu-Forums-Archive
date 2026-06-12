---
title: "Ethernet LAN cable not detected on Kubuntu"
date: 2018-01-02
forum: Networking &amp; Wireless
---

### Post by azazael2 on 2018-01-02
Hi all,

I hope I post this in the right forum and it hasn't been asked before - otherwise, sorry. This is my first post. I have found a lot of people with variations to the same problem online, but wasn't able to find a fix that actually works for me so far. So hoping that someone can give me some more individual advice. I am a complete newbie to Linux, so please excuse any stupid questions I might ask :?

I have Kubuntu installed on my HP Pavilion laptop (dual boot with Win10, from which I writing right now) and was trying to install the Realtek driver r8723de there following the instructions in [this post]("https://ubuntuforums.org/showthread.php?t=2367405&page=4"), now that it has finally been released. 

But turns out I don't even get so far, since I can't download things because I can't connect to the Internet using a LAN cable on Kubuntu either. Tried two different cables which both work on the Windows partition of my laptop, but not on Linux. What's weird is that it worked before, when I first plugged the cable in with Linux. I then downloaded some updates etc. and everything still worked fine. Switched the laptop off and tried it again another day. First thing that happened, the network connection completely crashed on every device. After a couple of restarts it worked fine again, except the ethernet cable wasn't found on my Linux device anymore. I presume some download that required a reboot to finish caused this, but I don't know for sure what happened.

I'm wondering if any of you guys can help me to get my Wifi running? Would be great to finally be able to actually use the Linux partition. Please let me know exactly what pieces of code/output you need. Thanks a lot!

---

### Post by praseodym on 2018-01-02
Lets check which hardware is in use:
```

uname -a
lspci -nnk
lsmod
```
Please c/p the outputs into a txt file and upload it.

---

### Post by azazael2 on 2018-01-03
Hi there,

the output I got for those commands is attached. Thank you!

---

### Post by praseodym on 2018-01-03
Wired driver is not loaded. Force it vie
```

echo r8168 | sudo tee -a /etc/modules
```
Reboot

---

### Post by azazael2 on 2018-01-03
I did, but it still doesn't find the network :( Any other ideas?

---

### Post by praseodym on 2018-01-04
Remove any connection in your network manager profiles, be sure being connected via cable, and reboot

---

### Post by azazael2 on 2018-01-06
There were no connections listed in the Network Manager anyway, so still no difference...

For "sudo lshw -C network" I get this output:

```
katharina@kathas-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:b4104000-b4104fff memory:b4100000-b4103fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b4000000-b400ffff

```

I read that "network unclaimed" means there is no driver claiming it, and that this could be fixed by downloading the latest versions of the respective drivers. But how would I be able to do that without a network connection?

---

