---
title: "Unable to get wifi working on Dell Vostro 200 (old computer)"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by mike237 on 2014-08-26
I just installed 14.04 on an old Dell that was headed to the recycling bin, and I cannot get the wifi to work.  Ethernet works.  I've tried following forums and I've downloaded two versions of the e1000 driver from intel that was mentioned as working for the Dell Vostro 200 on [this blog]("http://www.barryodonovan.com/index.php/2008/02/07/linux-dell-vostro-200").  

When I tried to install the newest version I got this error:
```
/bin/sh: 1: [: -ge: unexpected operator
Makefile:198: *** *** Aborting the build. *** This driver is not supported on kernel versions older than 2.4.0.  Stop.
```

When i tried to install an older version as mentioned on [this blog]("http://agileiscool.blogspot.com/2007/09/install-and-config-ubuntu-on-vostro-200.html"), I got this error:
```
Makefile:111: *** Linux kernel source not configured - missing version.h.  Stop.
```

I have a long cat-5 cable running down my hallway down the stairwell and plugged into the wifi router.  Any help on this matter would be greatly appreciated.

---

### Post by Vladlenin5000 on 2014-08-26
Hi, welcome.

That's the problem of following old tutorial, things often change. The drivers versions you tried to install are for very old Linux kernels. All are useless now and may break your system (unlikely - because you won't be able to install them anyway - but possible).

You shouldn't need any driver for such old card. Since Q2 2012 all you need should be in the kernel already. Are you sure the WiFi is working?

---

### Post by mike237 on 2014-08-26
Thanks for the reply.  When I unplug the ethernet cable I can't seem to get anywifi and my wifi network is not recognized.

What my network options look like on my desktop:
[ATTACH=CONFIG]255847[/ATTACH]

When I type in lspci:
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
```


And when I type in "sudo lshw -C network":
```
*-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:80:25:6d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.1-2 ip=192.168.1.110 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
```

I hope this helps get a little closer to a solution.  Thanks again.

---

### Post by Vladlenin5000 on 2014-08-26
I must ask again if you're sure it was working before?... Apparently not because it's not even listed. Linux is great but doesn't perform miracles like bringing back to like broken/faulty/disconnected/disabled hardware...

---

### Post by mike237 on 2014-08-26
Oh, no, it never worked.  This computer had windows vista on it and I replaced it with Ubuntu 14.04.  I am trying to get the wireless to work for the first time.  I'm assuming there's a wifi card in the computer, and that it's just a matter of getting the right driver for it, am I wrong?

---

### Post by Vladlenin5000 on 2014-08-26
I think you're probably wrong indeed. It's either not there or if it's there then at best is disconnected and/or disabled in BIOS and at worse faulty.

Linux is great but it doesn't do magic...

---

### Post by mike237 on 2014-08-26
oy.  well, thank you for the help and the clarification.

---

