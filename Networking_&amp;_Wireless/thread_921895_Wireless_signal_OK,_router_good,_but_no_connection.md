---
title: "Wireless signal OK, router good, but no connection"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by ALB628 on 2008-09-16
I am trying to access the internet through a home wireless network from this Ubuntu 8.04 installation I just set up last night, without success.

Everything else in the installation was easy and works.  Thanks a million!  A MS-free computer in my home!!!!

The wireless router (linksys WRT54G) works (Windows laptops continue to connect just fine), and I am able to run a wire from the ethernet card in this desktop to the router and get connected (that's how I'm here!  Hello!).

BUT... the problem looks like this:  Network manager icon seems to indicate that it can see the router - the name comes across, and there is a graphic indicator of reasonable signal strength.  

When I click the "linksys" radio button, dialog box for the WEP key comes up.  I enter the key, and there is still no live connection - firefox cannot see google.com. ubuntu.com, whatever. 

The dialog box asking for the key comes back up with the key empty. 

I don't think I can run the wire out the window all winter, so I'd like to figure this out.

Any ideas?

Here is text from the recommended routines to show hardware, drivers, etc,:

andrew@RCB:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
andrew@RCB:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
andrew@RCB:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wmaster0
       version: 01
       serial: 00:14:bf:78:89:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:07:e9:7c:a7:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
andrew@RCB:~$

---

### Post by mrsteveman1 on 2008-09-16
Is the router set for WEP or WPA?

Is it a hex key or a passphrase?

The only way im aware to use the same passphrase on every device is to use WPA2, because the method to generate that password is standardized.

WEP on the other hand, the passwords can differ. The only way to ensure you have the real key is to use the long hex code.

---

### Post by ALB628 on 2008-09-17
Thanks.  

We use this wireless router with numerous visiting windows laptops, and we use the same (long) hex key every time we get a new one hooked up.

So, I guess the answer to your question is:  It is WEP and hex key.

---

### Post by mrsteveman1 on 2008-09-17
That sounds like the issue, it might be expecting a passphrase or a different length key or something. You can set it manually though by right clicking the icon and clicking edit connections.

You should be able to set the key manually making sure it picks the right type, then it should work.

If not it might be a different problem but try that.

---

### Post by ALB628 on 2008-09-17
That did it.  I'm all set.

Many Thanks.  

-ALB628

---

### Post by mrsteveman1 on 2008-09-17
> **alb628 said:**
> that did it.  I'm all set.

Many thanks.  

-alb628

:)

---

