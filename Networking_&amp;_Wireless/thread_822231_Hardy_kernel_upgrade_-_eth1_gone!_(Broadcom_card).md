---
title: "Hardy kernel upgrade - eth1 gone! (Broadcom card)"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by sarahnwrap on 2008-06-08
Hi,

I have been using Hardy for a few weeks now, with no problems.  I upgraded my kernel the other day using auto update, and now my wireless card is not working.  eth1 is not recognized as a device. Previously I was using B43 as the wireless driver, but it's no longer loaded at startup.  I modprobe it, and it loads but doesn't solve the problem. Also, when I open up the restricted drivers manager (that is now the hardware manager) the Broadcom card is no longer listed.
Here is some output:

```
sarahn@thine:~$ uname -a
Linux thewb 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
```

```
sarahn@thine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:f5:81:38  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fef5:8138/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8719525 (8.3 MB)  TX bytes:1559976 (1.4 MB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11148 (10.8 KB)  TX bytes:11148 10.8 KB)


```

```
sarahn@thine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

I'm not sure what other information you would like...

Thank you.

---

### Post by avtolle on 2008-06-08
Does it still work if you boot to an earlier kernel?

---

### Post by Ayuthia on 2008-06-08
Unix_slayer mentioned in this [post]("http://ubuntuforums.org/showthread.php?t=779754") (but the post was edited while I was responding) that the new kernel update messed up some wlans and video.  For some reason, I was fortunate enough to not lose mine.

As avtolle mentioned, try the previous kernel and most likely you will be able to use your wireless.  If this is the issue, you can use that kernel until the next kernel update.  I would think that if this is happening on a lot of computers, a new kernel release will come out again soon that will fix this.

---

### Post by sarahnwrap on 2008-06-08
Thanks for the reply...
Actually yes, I tried rebooting into the previous kernel, but still had no luck.  B43 was loaded on boot, but eth1 was still not recognized.

---

### Post by Ayuthia on 2008-06-08
> **sarahnwrap said:**
> Thanks for the reply...
Actually yes, I tried rebooting into the previous kernel, but still had no luck.  B43 was loaded on boot, but eth1 was still not recognized.

When you go into the Terminal and type:
lshw -C network
does it provide a logical name for Wireless interface (does Wireless interface show up in description anywhere)?  You might also check /etc/udev/rules.d/70-persistent-net.rules and see if the card is listed there.

---

### Post by sarahnwrap on 2008-06-08
> **Ayuthia said:**
> When you go into the Terminal and type:
lshw -C network
does it provide a logical name for Wireless interface (does Wireless interface show up in description anywhere)?  You might also check /etc/udev/rules.d/70-persistent-net.rules and see if the card is listed there.

I get no output from lshw:

```
sarahn@thine:~$ lshw -C network
WARNING: you should run this program as super-user.
sarahn@thine:~$

```

Here is the line that references my card from /etc/udev/rules.d/70-persistent-net.rules:

```

# PCI device 0x14e4:0x4311 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:3a:54:95:48:3a", ATTR{type}=="1", NAME="eth1"

```

---

### Post by Ayuthia on 2008-06-08
> **sarahnwrap said:**
> I get no output from lshw:

```
sarahn@thine:~$ lshw -C network
WARNING: you should run this program as super-user.
sarahn@thine:~$

```

Does lspci show anything for your wireless card?

---

### Post by sarahnwrap on 2008-06-08
No, I dont get anything from lspci either:
```
sarahn@thine:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by Ayuthia on 2008-06-08
> **sarahnwrap said:**
> No, I dont get anything from lspci either
I don't see it either.  It almost looks like your card is no longer working for some reason.  Are you dual booting?  If so, are you able to get your wireless to work on it?  Also if you have the live CD, try booting from it and see if it finds your wireless.  If neither one of them see your wireless, I am thinking that your card died or somehow the card got loose.

You might even check the BIOS and see if there is anything for your wireless card.

If it does work with the live CD or through another operating system, then something in the previous update is causing the wireless card to not be detected.  So you could backtrack and see what was recently updated and try to figure out what caused this, you could reinstall, you could wait for another update and see if it fixes it, or you could see if someone else has another idea.

Since you said that the previous kernel does not work either, I would say that it was not the kernel update, but another package.  To point out the obvious, it would most likely be a package that does not need a kernel compile (any package that does not have a 2.6.24 extension).

---

### Post by sarahnwrap on 2008-06-09
I checked the BIOS and didn't see any card detected there.  I am not dual-booting, so I dont have another OS to test my card against.  I think that based on this, my card just happened to have died at about the same time I did a kernel update.  Completely coincidental.  I'm not terribly surprised, it was giving me some connectivity issues beforehand.
Thanks so much for the troubleshooting help, Ubuntu forums gets me through lots of weird laptop issues :)

---

