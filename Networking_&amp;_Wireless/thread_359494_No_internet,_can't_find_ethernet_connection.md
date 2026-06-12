---
title: "No internet, can't find ethernet connection"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by rob_909 on 2007-02-12
I'm pretty new at linux, and I just installed dapper. I went to Network Settings and it doesn't detect my ethernet connection. I am going through a router if that makes any difference........but all I see is a modem connection

ifconfig:

lo         Link encap;Local Loopback
           inet addr: 127.0.0.1 Mask: 225.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436  Metric:1
           RX packets:279 errors:0 dropped:0 overruns:0 frame:0
           TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:20984 (20.4KiB)   TX bytes: 20984 (20.4 KiB)

Do I need to get install drivers or something, forgive me, this is probably an easy fix.

---

### Post by gradedcheese on 2007-02-12
Yeah, it looks like you may need drivers.  Please post the output from running "lspci", namely lines starting with something like Ethernet Controller.  Also, just to check: this is a PCI or PCMCIA card, not ISA, right?

---

### Post by rob_909 on 2007-02-12
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
0000:00:19.0 Ethernet controller: Intel Corporation: Unknown device 104c (rev 02 )
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2812 (rev 02)
0000:00:1f.2 RAID bus controller: Intel Corporation: Unknown device 2822 (rev 02 )
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d1 (rev a1)
0000:03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem

yeah pci card....

that is a lot of unknown devices.......

---

### Post by rob_909 on 2007-02-12
Also, this is a Dell E520. I read a few other forums and other people seem to be having the same problem.....lots of unknown devices. I think I found the driver  (Intel® 82562 Fast Ethernet Controllers Downloads) but I dont know which one it is, or how to install the driver. Many people are saying that a kernel update would fix the drivers for me, how does that work?

---

### Post by gradedcheese on 2007-02-12
For that chipset, I think you need this driver:

[http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54834](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54834)

However I am not really sure, so please check if the e100 driver is right.  If it is, download that.  You're going to have to have kernel source to build it, which is probably going to be an interesting experience for you :)  For now,

sudo apt-get install build-essential kernel-headers-`uname -r` kernel-source-`uname -r`

would be a good start.

---

### Post by rob_909 on 2007-02-12
How do I do an apt-get without the internet?

---

### Post by gradedcheese on 2007-02-12
If the packages are on the ubuntu CD (I am not sure if they are), you can just put in the CD, open Synaptic, and choose 'repositories' from the 'settings' menu to add the CD as a repository.  From there you can close Synaptic and use apt-get, or use Synaptic itself to grab packages.  Otherwise, you can go to another PC and download the packages manually, bring them over, and:

sudo dpkg -i /path/to/package/here

(packages end in ".deb")

---

### Post by rob_909 on 2007-02-13
Found driver, it was the e100 driver. Got distracted by super mario world and never installed it, but I have the file on there now. I have a friend that knows linux better than his own family that is going to fix me up hopefully with various things, i'll let you know how it goes..........as for right now my main concerns are
- get internet
- get 686-smp kernel (i can do this)
- get high resolution for 22'' monitor
- get to read from ntfs partition (i can do this)
- aiglx or xgl/beryl (i think i can do this....when I get an nvidia update, though I have heard it has problems on the e520)
- finish mario

---

### Post by rob_909 on 2007-02-14
i fixed everything, everything works

---

