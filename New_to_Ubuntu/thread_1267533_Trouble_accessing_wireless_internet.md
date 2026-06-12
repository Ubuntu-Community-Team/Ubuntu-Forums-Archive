---
title: "Trouble accessing wireless internet"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by millbiller on 2009-09-15
Hi all!  I'm a new Ubuntu 9.04 user (installed yesterday).  I'm having trouble accessing the internet through my wireless router (NetGear WGR614v4).  Internet works fine when hard-wired to the router.  Also, I'm able to access wireless when booting Windows.  Here's my hardware:
 
Toshiba Satellite A505D
AMD Turion x2 Ultra Dual-Core Mobile ZM-84 processor, 64-bit
Realtek RTL8102/8103 Family PCI-E FE NIC
Realtek RTL8192E Wireless LAN 802.11n PCI-E NIC
NetGear WGR614v4 router
 
Any help will be greatly appreciated!!:)

---

### Post by gettinoriginal on 2009-09-16
Hi, and welcome to Ubuntu  :P   Try [here]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")

---

### Post by sandyd on 2009-09-16
from a quick search on google, you mostly will have to use ndiswrapper to get it running.

EDIT: found instructions

```

Just install Ndiswrapper with Synaptic, download Windows XP driver for Samsung n120 wifi card Realtek 8192 (you can find it on samsung webpage) and unpack it, and then just find unpacked net819xp.inf file with ndiswrapper and it should work (off course you need to set up your wifi functions like ssid, password etc.) Ndiswrapper may say that it couldn't find the device, but it works.
Good luck.

```don't use the realtek driver from the site. seems like it doesn't work for everybody

orngional thread [http://ubuntuforums.org/showthread.php?t=1191590](http://ubuntuforums.org/showthread.php?t=1191590)

---

### Post by HarrisonNapper on 2009-09-16
For this, you might also try adding a notification area on your taskbar; I'm not sure why, but it worked for me on my new laptop (with which there are a number of problems to begin with). For some reason, the network manager doesn't work while the app that runs in the notification area does. Try adding the notification area (Right click, Add to Panel, Notification Area, Add, Close), if that doesn't work, install ndiswrapper (sudo apt-get install ndiswrapper), and if that doesn't work let us know and we can see what's up. Ndiswrapper didn't work for one of my older Compaq Presario laptops (which is now in Davy Jones' Chipbin) and I had to implement a fun work around.

---

### Post by tonyps on 2009-09-25
Morning,
 
Do you know if there has been any recent success with getting this to work under the Ubuntu 64bit version....with the Realtek RTL8192e?
 
Thanks bunches!!
 
Tony ...

---

### Post by random turnip on 2009-09-25
Can you actually see your router and have you done all updates?

If you can't see the router or any other available wireless networks then you will probably need to used Ndiswrapper.  But just because you have it set to automatic or remember on Windows, it won't make Ubuntu recognize it automatically, you will need to select it and type in the password again.

---

### Post by millbiller on 2009-09-25
Thanks to everyone who is giving out the help.  However, I haven't been successfull at all.  I have installed ndiswrapper with the util, common packages along with the ndis gui, ndisgtk.  Now when I go to the Systems>Admistration menu there is an app called Windows Wireless Drivers.  I click on it and it eventually finds the net819xp driver, but still no wireless.  I'm very green when it comes to Linux, especially the command line.  I don't even know enough to be dangerous - just extremely dangerous:-).  So, I'm still at square one, although I've been learning a bunch.  Any help from the Linux gurus, especially Jaunty, would continue to be appreciated.  It would also be helpful if is was sent with line-by-line instructions.

Thanks again!!!

---

### Post by bkratz on 2009-09-25
> **millbiller said:**
> Thanks to everyone who is giving out the help.  However, I haven't been successfull at all.  I have installed ndiswrapper with the util, common packages along with the ndis gui, ndisgtk.  Now when I go to the Systems>Admistration menu there is an app called Windows Wireless Drivers.  I click on it and it eventually finds the net819xp driver, but still no wireless.  I'm very green when it comes to Linux, especially the command line.  I don't even know enough to be dangerous - just extremely dangerous:-).  So, I'm still at square one, although I've been learning a bunch.  Any help from the Linux gurus, especially Jaunty, would continue to be appreciated.  It would also be helpful if is was sent with line-by-line instructions.

Thanks again!!!


Didn't really understand the "eventually finds it " you have to point it at the .inf file
Don't worry if it makes some comment like hardware not found at this point, it always seems to show up.Once you have added the .inf file it will say something like Harware pressent--yes.  Don't worry if it says Configuration tool not found it you pressed Configure network.
At this point you should have four vertical bars on the top panel prbably next to the speaker ( I moved mine and I don't remember the original position).
Right click on the bars and check mark the enable wireless box.

Select edit configuration here is where you actually setup the network. If you need help here just post back. Some box on these menus allows you to make the connection available to all users. Click it ( otherwise you will get a pesky put in your password message forever).
If you left click on the bars (after you finish setup ) you should see your network and click on it, follow the instructions which come up.

Good Luck,

---

### Post by rustutzman on 2009-09-25
> **millbiller said:**
> Thanks to everyone who is giving out the help.  However, I haven't been successfull at all.  I have installed ndiswrapper with the util, common packages along with the ndis gui, ndisgtk.  Now when I go to the Systems>Admistration menu there is an app called Windows Wireless Drivers.  I click on it and it eventually finds the net819xp driver, but still no wireless.  I'm very green when it comes to Linux, especially the command line.  I don't even know enough to be dangerous - just extremely dangerous:-).  So, I'm still at square one, although I've been learning a bunch.  Any help from the Linux gurus, especially Jaunty, would continue to be appreciated.  It would also be helpful if is was sent with line-by-line instructions.

Thanks again!!!

Since you have just installed this and don't have too much involved yet I think I'd give the latest kernel a try. I have found that it is much more friendly with wireless. Download the latest alpha [http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/) and give the Live CD a spin. If everything works do a new install with it. I have been pushing it pretty hard and find it very stable and all of my hardware worked out of the box. Just an idea.

Russ

---

### Post by zipperback on 2009-09-25
Post up the results from the following commands:

```

lsusb
lspci
ifconfig
iwconfig

```

Also please tell us if you're using WPA or WEP for your wifi connection authentication.

- zipperback
:popcorn:

---

### Post by millbiller on 2009-09-26
zipperback, here is the info you requested:
 
lsusb:
Bus 002 Device 002: ID 064e:d104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
05:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
05:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
 
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1e:33:df:84:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0x2000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3424 (3.4 KB)  TX bytes:3424 (3.4 KB)

iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
 
 
 
again, any help is appreciated!

---

### Post by millbiller on 2009-09-30
Still haven't been able to get my Realtek card to work.  I am able to connect via a USB adapter (Linksys).  Ubuntu recognized it right away.  However, I consider this a short term fix - especially since it is usually attached to my daughter's PC.  Would like to be able to get the Realtek card to work.

---

### Post by djyoung4 on 2009-09-30
did you check to see if the standard driver is working.  go to system -> administration -> hardware drivers and see if the driver is activated.  I didn't see anybody suggest that so if you have already tried that then I have no idea

---

