---
title: "Driver Installation Procedure Confusion"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by seano33 on 2010-03-28
So I'm totally confused. The simplicity of the Mac is not so here in Ubuntu world. I did a fresh install of 9.10 on an Intel P4 with a Linksys PCI Wireless card previously installed. I purchased this used and put it in before doing the OS install. Now, as far as locating a driver, I believe I have download the correct package from [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/) and B49 should be the driver. What turned me off from Linux years ago was all the manual installation procedure and the lack of good available software. Now the software is good, but how about the simplicity of making installations? And what about the assumptions that are made by experienced Linux users? Nobody seems to start from the beginning confused mind of a Mac user who can click and drag like a pro but is lost with this coding. So to my main question...

Is there a single, simple way of installing this driver package? 

Please help me someone, and make this simple for everyone's benefit. My head is melting, and I'm not alone. I have a friend with the exact same issue. In fact, I've read that this problem is common.

---

### Post by cariboo on 2010-03-31
Are you sure the card isn't detected and the driver loaded already? Open an Application->Accessories->Terminal and type:

```
sudo lshw -C network
```

you should see an output similar to this:

```
sudo lshw -C network
[sudo] password for me: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:62:eb:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=full ip=192.168.1.250 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febe0000-febfffff(prefetchable)
```

Look for something that looks like what I have bolded in the output above.

---

