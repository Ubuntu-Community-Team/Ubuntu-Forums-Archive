---
title: "Infamous Wireless trouble"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Sheneron on 2009-03-20
Hi,

I am running the latest release of ubuntu on my Gateway MT3705 laptop computer.  My wireless generally works except for one issue.  If I have accept a security certificate the wireless just disappears completely rendering my computer unable to connect to a wireless network. This is a problem because I go to a college and I have to accept a security certificate in order to connect.

Now, I have heard about a fix using ndiswrapper and a windows xp wireless driver.  The problem is that I can't find the driver online.  I can only find an exe file and not an inf file.  I have looked at various threads on here, but the links to the drivers seem dead, and if they do work they don't point to an inf file.  Can anyone help me?  Thank you so much

---

### Post by avtolle on 2009-03-20
You need to extract the .inf (and possibly the .sys) file(s) from the .exe file. No, I haven't done this, as I've not needed to; but the above is from reading other threads here on the Forum about how this is accomplished.

---

### Post by lkraemer on 2009-03-20
Sheneron,
Do you still have Windows installed on your Gateway MT3705?  If you do,
you should be able to go to the Control Panel and progress down through
the system to the Wifi Driver.  Once you find the driver you will need
the inf and same named sys file.  They are most likely located at
C:/windows/system32 if my memory serves me right.

Or you can post the output of the following:
```

lspci
lsusb
lshw -class network
uname -a
lsb_release -a

```

That will give folks a clue as to what hardware you have.

ref:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

lkraemer

---

### Post by Sheneron on 2009-03-22
Well, I found a driver installed it and it works.  However, I am still having trouble accepting security certificates.  If I do so my whole wireless completely drops and I have to restart or log out and back in.

Here is what I get when I type those in..

steve@pebblerebel:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

steve@pebblerebel:~$ lsusb
Bus 003 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

steve@pebblerebel:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:41:ec:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:d1:78:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.53+Realtek,04/13/2006,5.1060.0 ip=192.168.1.5 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:d2:d5:37:cc:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

steve@pebblerebel:~$ uname -a
Linux pebblerebel 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

steve@pebblerebel:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:languages-3.2-ia32:languages-3.2-noarch:multimedia-3.2-ia32:multimedia-3.2-noarch:printing-3.2-ia32:printing-3.2-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid


Thanks for the help so far!

---

### Post by Sheneron on 2009-03-27
Anyone?

---

### Post by lkraemer on 2009-03-28
Well,
Now we know that your wireless is  the following:
```

description: Wireless interface
product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.

```

So, if I read your post correctly you want to stop using the current
(out of the box driver) and want to use ndiswrapper and the Windows
driver for the RTL-8185 Realtek Interface.

Is that correct?  What will that gain you?  

A SEARCH of this forum finds:
[http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy)
[http://www.willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy](http://www.willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy)

and this one:
[http://ubuntuforums.org/showthread.php?t=772006&highlight=Howto+RTL-8185](http://ubuntuforums.org/showthread.php?t=772006&highlight=Howto+RTL-8185)

I would try the above before going to ndiswrapper.

lkraemer

---

