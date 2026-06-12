---
title: "New Install.  Can't connect!"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by waste301 on 2009-08-27
Newbie here.  Fresh install.  I cant connect to a wireless network, it is not detecting anything.  lspci shows this:

lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

sudo lshx -C network shows this:

description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:7e:06:32:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:80:39:24:29:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
matt@matt-desktop:~$ network:0 e


I don't know how to enable the connection or if I need a driver or what.  Please help.

---

### Post by Liolikas on 2009-08-27
Interesting... you should search forums about this:
01:09.0 Network controller: **Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ALSO:
Show ifconfig, iwconfig.

---

### Post by waste301 on 2009-08-27
> **Liolikas said:**
> Interesting... you should search forums about this:
01:09.0 Network controller: **Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ALSO:
Show ifconfig, iwconfig.

I searched.  It looks like I might need to enable broadcom drivers?
I went to hardware drivers and all it asks me is if I want to enable drivers for my graphics card, which it then cannot do because it can't connect to the internet.  The the driver manager closes.

---

### Post by Liolikas on 2009-08-27
Most simple solution is to get temporary LAN network and then enable drivers. If this is impossible for you write here.

---

### Post by zerhacke on 2009-08-27
I have the same card.  You can use ndiswrapper with them very easily and the connection is top notch.  I'll attach my drivers to this message, they are the 32 bit drivers.  I can help with the 64 bit drivers too, if that's what you need.

---

### Post by waste301 on 2009-08-27
> **Liolikas said:**
> Most simple solution is to get temporary LAN network and then enable drivers. If this is impossible for you write here.

Unfortunately I cannot.  I can log onto the wireless network in Windows and download whatever I need onto a thumb drive and then boot into ubuntu and install.  That is what I just did to get these for you:

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:da:d7:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)


iwconfig gave me this:

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:da:d7:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)


Hope this can help in some way, as I sure as hell don't know what it means.

---

### Post by Liolikas on 2009-08-27
That shows working WLAN card.
Try simple command-line wireless scan:
iwlist scan

---

### Post by zerhacke on 2009-08-27
Using these cards natively requires fwcutter and the Windows drivers anyways.  It will see the card but will not attach a driver without fwcutter and a whole host of techy stuff that is just better handled by ndiswrapper.

If you can't get internet except through windows, download the ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk deb packages and install them manually.  With ndisgtk you will have a gui app to install the ndiswrapper drivers with.

Good luck!

---

### Post by zerhacke on 2009-08-27
> **Liolikas said:**
> That shows working WLAN card.
Try simple command-line wireless scan:
iwlist scan

There is nothing listed above that shows a working wlan0.

---

### Post by Liolikas on 2009-08-27
> **zerhacke said:**
> There is nothing listed above that shows a working wlan0.

Hmm there is:
> 
wconfig gave me this:

eth0 Link encap:Ethernet HWaddr 00:1f:c6:da:d7:76
**UP **


---

### Post by zerhacke on 2009-08-27
eth0 is ethernet.  Wireless would be wlan0.

---

### Post by Liolikas on 2009-08-27
Not always: my wireless is eth1 too.
BUT i**w**config should show only wireless always.

---

### Post by waste301 on 2009-08-27
> **zerhacke said:**
> I have the same card.  You can use ndiswrapper with them very easily and the connection is top notch.  I'll attach my drivers to this message, they are the 32 bit drivers.  I can help with the 64 bit drivers too, if that's what you need.

For some reason it is downloading at 1.1 kb a second.  If I get it can you tell me how to install it?

---

### Post by waste301 on 2009-08-27
> **zerhacke said:**
> Using these cards natively requires fwcutter and the Windows drivers anyways.  It will see the card but will not attach a driver without fwcutter and a whole host of techy stuff that is just better handled by ndiswrapper.

If you can't get internet except through windows, download the ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk deb packages and install them manually.  With ndisgtk you will have a gui app to install the ndiswrapper drivers with.

Good luck!

Can you tell me where/how to download these onto my thuimb drive and then install them and run them?

---

### Post by zerhacke on 2009-08-27
> **Liolikas said:**
> Not always: my wireless is eth1 too.
BUT i**w**config should show only wireless always.

Wow, I did not know that.  However, I know the card he has, he either has to get the drivers and use fwcutter on the drivers or use ndiswrapper to install.  It'll look like the card is active but it is not.

---

### Post by zerhacke on 2009-08-27
> **waste301 said:**
> Can you tell me where/how to download these onto my thuimb drive and then install them and run them?

I'll provide a download link right away, as soon as I find it.

---

### Post by zerhacke on 2009-08-27
[http://packages.ubuntu.com/jaunty/net/](http://packages.ubuntu.com/jaunty/net/)

---

### Post by waste301 on 2009-08-27
> **zerhacke said:**
> [http://packages.ubuntu.com/jaunty/net/](http://packages.ubuntu.com/jaunty/net/)

Thanks!  I downloaded the i386 version of ndisgtk.  I'm going to boot into ubuntu and try and install it.  BRB.

---

### Post by waste301 on 2009-08-27
> **zerhacke said:**
> [http://packages.ubuntu.com/jaunty/net/](http://packages.ubuntu.com/jaunty/net/)

I am getting this error when I double click on the .deb file:

**error: dependancy is not satisfiable: ndiswrapper-utils-1.9**

---

### Post by zerhacke on 2009-08-27
You have to download all three packages I mentioned.

---

### Post by waste301 on 2009-08-27
> **zerhacke said:**
> You have to download all three packages I mentioned.

Progress! ndisgtk is up and running, but it is asking me for a .inf file.

The bmc4310.tar.gz file from your original post took forever to download and will not open.  Is that the.inf file I need?

---

### Post by waste301 on 2009-08-27
> **waste301 said:**
> Progress! ndisgtk is up and running, but it is asking me for a .inf file.

The bmc4310.tar.gz file from your original post took forever to download and will not open.  Is that the.inf file I need?

Bump.  I just need the right .inf file now I think.  Can anyone help me find it? Looking.

---

### Post by waste301 on 2009-08-27
Still no luck connecting, any help out there?

---

### Post by waste301 on 2009-08-27
bump

---

### Post by zerhacke on 2009-08-27
I'm back from lunch.  Sorry to keep you hanging.

Did you manage to get all three .deb files installed on your Linux side?  If you have, Ubuntu will open a .tar.gz file like it is a .zip file that I'm sure you're familiar with on Windows.  Simply right click the .tar.gz file I provided and press extract (I promise it is not a bomb).  Then look for the inf file that is produced from extracting that tar.gz.  Note, this set of files is for a 32 bit operating system.  If you are using a 64 bit operating system I can still help.  I just didn't include the 64 bit sys file as it makes the download too big to attach on this forum.

---

### Post by waste301 on 2009-08-27
> **zerhacke said:**
> I'm back from lunch.  Sorry to keep you hanging.

Did you manage to get all three .deb files installed on your Linux side?  If you have, Ubuntu will open a .tar.gz file like it is a .zip file that I'm sure you're familiar with on Windows.  Simply right click the .tar.gz file I provided and press extract (I promise it is not a bomb).  Then look for the inf file that is produced from extracting that tar.gz.  Note, this set of files is for a 32 bit operating system.  If you are using a 64 bit operating system I can still help.  I just didn't include the 64 bit sys file as it makes the download too big to attach on this forum.

Hey, thanks for getting back.  Yeah, I got all three .deb files installed and under system--->admin I now have a "windows wireless drivers" tool.

Problem:  When I try to open the tar.gz file I get this error:


gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

Also, when I open the tool, it says:  Unable to see if hardware is present

Although there is a driver there now (I've been trying a few other things while you were gone)

---

### Post by zerhacke on 2009-08-27
What's the name of the driver you have installed?  You might have the right one.  Odd that my tar.gz file is corrupt... I just made it literally from the drivers I have on my system.

I remember that on our card, it will tell you that it can't find the hardware even if it is there.  Don't panic, it's a feature, not a bug.

---

