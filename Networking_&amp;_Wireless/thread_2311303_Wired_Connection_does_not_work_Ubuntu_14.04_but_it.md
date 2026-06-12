---
title: "Wired Connection does not work Ubuntu 14.04 but it works Windows 8.1"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by Y.E.S. on 2016-01-26
Hi everyone;


I have a problem with wired connection as I said on title. Actually, wired connection works first installation Ubuntu. However, after reboot or switch to Windows, it does not work. By the way, with Ubuntu LiveUsb, connection work.

```

 sudo lshw -C network
      *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: bc:ee:7b:da:2c:ad
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:27 memory:f7c00000-f7c1ffff memory:f7c3d000-f7c3dfff ioport:f080(size=32)

```

---

### Post by chili555 on 2016-01-26
> However, after reboot or switch to Windows, it does not work.Heard of this, we have...

I strongly suspect that this has to do with either the BIOS or Windows being set to allow Wake-on-Lan. Does it work if you cold-boot to Ubuntu? Is there a WOL setting in the BIOS? Try changing it; in other words, if it's off, turn it on and vice-versa.

Is there a WOL setting in Windows?

I can't tell you where to look, I haven't a Windows computer.

---

### Post by andrei90 on 2016-01-26
Try in terminal

```
[COLOR=#222426][FONT=Arial]sudo service network-manager restart[/FONT][/COLOR]
```

---

### Post by Y.E.S. on 2016-01-28
Unfortunately, there is no option Wake-on-Lan or something like that. Also, I think, there is no option Wake-on_Lan in Windows. There is a fastboot option in Windows and it turns off.

---

### Post by Y.E.S. on 2016-01-28
I tried many times before, but it does not troubleshoot.

---

### Post by chili555 on 2016-01-28
> **Y.E.S. said:**
> Unfortunately, there is no option Wake-on-Lan or something like that. Also, I think, there is no option Wake-on_Lan in Windows. There is a fastboot option in Windows and it turns off.Are you quite certain?  [http://thewindowsclub.thewindowsclubco.netdna-cdn.com/wp-content/uploads/2013/10/Wake-on-LAN.jpg](http://thewindowsclub.thewindowsclubco.netdna-cdn.com/wp-content/uploads/2013/10/Wake-on-LAN.jpg)

What about cold boot? Is there any change in the behavior?

---

### Post by Y.E.S. on 2016-01-29
Thanks for your helping. I solved the problem. Problem is about driver ethernet card on Windows. I realize that the problem begins after start the Windows with your guidance and update ethernet driver on Windows. After that, it works correctly.

---

### Post by chili555 on 2016-01-29
Awesome! Glad it's working!

---

