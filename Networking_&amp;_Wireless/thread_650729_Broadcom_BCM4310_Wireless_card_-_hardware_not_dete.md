---
title: "Broadcom BCM4310 Wireless card - hardware not detected"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by kertrats on 2007-12-26
Clearly, the broadcom bcm43xx network cards are a common problem; I've read many threads in the last several hours trying to get my new laptop (Dell Inspiron 1520) to pick up wireless with Gutsy. I've installed ndiswrapper, have blacklisted the bcm43xx drivers in /etc/modprobe.d/blacklist, have installed the windows drivers for bcmwl5.  However, wireless is still not even showing up anywhere, much less working.

The physical network switch is definitely on, and it works when I boot into my Windows XP partition.  When I open System-Administration-Network, it doesn't even show a wireless connection, only Wired and Modem.  

Some results I've already gotten:

lspci | grep Broadcom gives:

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

What I believe to be the relevant section of lshw:

           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:09:b4:2d:72
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.10.9 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s

/etc/network/interfaces only contains:

auto lo
iface lo inet loopback



While I've used Linux before, this is my first time attempting to install it myself, so I might be missing something obvious.  Any help would be greatly appreciated.

---

### Post by branx503 on 2007-12-26
It looks like you and I are in the exact same boat (dell inspiron 1520 and everything)... I'm still in the process of working it out, but take a look: [http://ubuntuforums.org/showthread.php?t=649237]("http://ubuntuforums.org/showthread.php?t=649237")

---

### Post by JamesGu on 2008-01-15
I have the exact same card on my Dell Vostro 1500 and finally got it working. For reference, here's my lspci:

```
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```

And lshw -C network:

```
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:48:56:2d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,09/20/2007, 4.170. ip=192.168.1.41 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

I followed the instructions from dell, here:

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Using the driver from here:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=12&l=en&s=bsdv&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=4&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&cs=12&l=en&s=bsdv&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=4&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819)

(Direct link: [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) )

When you unzip this, you'll have a DRIVER_US directory which contains the right file to use.. (bcmwl5.inf).

Hope this helps!

---

### Post by broken+broken on 2008-01-18
JamesGu-
Oh my god...  thank you so much!!!  I have been pulling my hair out with this card.  I know that broadcom is a pain (several other installs) but this was just insane.  I had followed the same general steps to get this card working with ndiswrapper but all others failed.  I think the key was finding the right driver, for me at least.  Works like a champ now.  Thanks again.

Specs:
hp pavilion dv2000 series,  dv2710us
AMD dual 2.0 64 bit
ubuntu 7.10 64 bit version
Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

JamesGu- if you send me your mail addy I'll send you some cookies.

---

### Post by txbikerider on 2008-01-26
What driver did you use and where did you get it?  

I've been struggling with this for a day now and have had no success.

---

### Post by Limbic on 2008-02-04
I've got pretty much an identical system to broken + broken  (a DV2715 with AMD CPU and Broadcom 4310 wireless), but haven't had any luck at all with any of the many different things I've tried.  I'm a complete Linux novice, so it's likely something I'm screwing up on my end.  Unfortunately, I have no idea what that is.  Here are are the results of the error check you perform as the last step on the instructions listed at[ Dell support]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper"):
> 
tail /var/log/messagesFeb  4 21:29:22 sbl-laptop kernel: [   21.844000] Bluetooth: RFCOMM ver 1.8
Feb  4 21:29:22 sbl-laptop kernel: [   22.000000] Clocksource tsc unstable (delta = -83383545 ns)
Feb  4 21:29:24 sbl-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth15 for sub-path eth15.dbus.get.reason
Feb  4 21:29:28 sbl-laptop kernel: [   27.456000] NET: Registered protocol family 17
Feb  4 21:29:33 sbl-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth15 for sub-path eth15.dbus.get.host_name
Feb  4 21:29:33 sbl-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth15 for sub-path eth15.dbus.get.domain_name

I've tried so many different ways to do this, I think it's probably just likely I've got a whole bunch of accumulated crap in there, so I'm considering just re-installing Ubuntu again and starting from scratch.  That said, any help at all that would make that unnecessary would be much appreciated, and yes, I will also send cookies.  :)

---

### Post by britgamer on 2008-02-16
Thanks JamesGu that dell guide worked wonders on my hp530 (using the dell driver too).

> **Limbic said:**
> I've got pretty much an identical system to broken + broken  (a DV2715 with AMD CPU and Broadcom 4310 wireless), but haven't had any luck at all with any of the many different things I've tried.  I'm a complete Linux novice, so it's likely something I'm screwing up on my end.  Unfortunately, I have no idea what that is.  Here are are the results of the error check you perform as the last step on the instructions listed at[ Dell support]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper"):


I've tried so many different ways to do this, I think it's probably just likely I've got a whole bunch of accumulated crap in there, so I'm considering just re-installing Ubuntu again and starting from scratch.  That said, any help at all that would make that unnecessary would be much appreciated, and yes, I will also send cookies.  :)

Did it say anything underneath those error messages? I got similar error messages but other messages beneath it saying that my card was found and what encryption it supported etc.

here is (hopefully) the relevant section from my /var/log/messages:

Feb 16 16:31:13 richard-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb 16 16:31:13 richard-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Feb 16 16:31:13 richard-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 16 16:31:13 richard-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb 16 16:47:07 richard-laptop kernel: [ 4131.236000] ndiswrapper version 1.45 loaded (smp=yes)
Feb 16 16:47:08 richard-laptop kernel: [ 4131.660000] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
Feb 16 16:47:08 richard-laptop kernel: [ 4131.660000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 16 16:47:08 richard-laptop kernel: [ 4131.672000] ndiswrapper: using IRQ 17
Feb 16 16:47:08 richard-laptop kernel: [ 4131.872000] wlan0: ethernet device 00:1a:73:e5:17:59 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: '', 14E4:4315.5.conf
Feb 16 16:47:08 richard-laptop kernel: [ 4131.872000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb 16 16:47:08 richard-laptop kernel: [ 4131.872000] usbcore: registered new interface driver ndiswrapper

I think the jump in the time is due to "sudo depmod -a" taking ages to do whatever it was doing.

---

### Post by Limbic on 2008-02-16
Thanks for checking in, I got this figured out and meant to post about it but forgot.

Anyway, the issue was actually a problem with a bad installation of NDISWrapper; the driver mentioned above actually worked just fine.  My previous post was actually within just a few days of me using Linux for the first time, so I think I misunderstood or skipped over something in the process.  Here are a few quick bullets for future reference if anyone else runs into the same issue.
[B]
Problem #1:  Don't overcomplicate![/B]  I read a whole bunch of different threads and advice about how to get everything working, assumed the worst would happen, then went from there.  I followed the instructions for working at the most fundamental level with the drivers and tried to compile the newest version of NDISWrapper from source.

This was my big mistake; I think i was pointing to the wrong folders or something during the install, but it never compiled quite correctly, so that even when I got NDISWrapper installed and (I thought) working, it wasn't correctly controlling the hardware.  I'd get a message from iwconfig that the driver was present but the hardware wasn't found.  I was also getting messages that I was using the incorrect driver even when I was using the driver I'm using to post this right now.

I also tried the BCM43xxx firmware, both compiling from source and grabbing the version from the repositories.  This may just be a bad choice for my particular wireless card (Broadcom 4310 (rev 1)) because I still couldn't get it working in any configuration.

**Solution:**  I tried a fresh install of Ubuntu, grabbed the newest available version of NDISWrapper from the Synaptics Package Manager, pointed it to the right driver and voila! everything worked just fine right off the bat.  Also, I've been playing around with other distros a bit, and the version of NDISWrapper that comes with LInux Mint (based off Ubuntu) worked just fine out of the box.  All I had to do was point it to the driver and it was working within just a few minutes of the completed OS install.

So hopefully this'll help if someone else runs into my same problems, and thanks, Britgamer.  :)

---

### Post by Elvje on 2008-02-22
> **britgamer said:**
> Thanks JamesGu that dell guide worked wonders on my hp530 (using the dell driver too).

Hei,

You say it works on your HP 530... So I tried it too, but it doesn't work. Please help me, I try for 2 days now and I'm going grazy :?

---

### Post by keenwerkz on 2008-02-27
im using HP DV2715nr, i did the whole process (jamesgu's reply) and it worked. im writing this using the wireless access in my laptop...

basically it never worked the first time since i was not using a fresh install, i tried all the other means (ndiswrapper instructions from other threads, fwcutter) and then this... none worked... 

i was about to give up when i thought about trying it on a freshly installed system...

installed ubuntu (ubuntu 7.10 amd64)
downloaded nvidia-glx-new
downloaded ndisgtk using synaptics (it will automatically install ndiswrapper common and utils)
extracted the dell drivers in /tmp/bcm43xx (DRIVER_US directory)
followed the install instructions
checked system->admin->network and found wireless connectivity
restarted my laptop
viola i can access the wireless network!!!

never been happier!!!

as a side note when i installed ubuntu in my laptop (1st install) the switch was turned off, in my most recent installation i left it on. I don't know if it somehow also helped but i noticed some threads especially on audio devices that when the device is turned off while in windows it won't function in linux so i just turned it on during the reinstallation.

---

### Post by scotc on 2008-03-03
system: Broadcom BCM4310 usb controller (rev 01) Wireless card in Vostro 1500

Thanks for your post JamesGu,
I has helped me to get my wireless working.  I also needed Paperdiesel's Howto, as it is more for newbies.
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092).

Worth noting:  this driver has USA, Japan and Rest Of World varieties. They are all in the driver.exe file though.

---

### Post by mgmdvm on 2008-03-05
I have an HP DV2745se, with the BCM4310 card.  I am new to Linux and Ubuntu.  I tried the XP and Vista drivers for the wireless, with no luck.  When I list the drivers, I see the driver is installed, but nothing about the hardware.  I have tried all of the instructions and How tos that I saw in this thread, but no luck.  Do I need to reinstall Ubuntu (I am using 7.10) and start completely over?  If so, do I just do a new install over the old install, or do I need delete the old install?  I am very new to Linux, so any help is appreciated.

---

### Post by mgmdvm on 2008-03-05
Did a fresh install of 7.10, followed the how to for my wireless, and it works!  But now when I boot into Vista, the wireless won't look for a network.  Windows says it is working properly, the light is on, etc, but will not even try to connect to a network.  Any suggestions for a new Linux user?

---

### Post by borahshadow on 2008-03-13
Thanks JamesGu. I had ndiswrapper installed but it wouldn't play nice with the newest driver for my vostro 1000 (same card as this thread, or dell 1395) and the older drivers I found didn't work with this card. I just needed the driver you posted and it worked thanks.

mgmdvm: is the card not working in vista or linux?

---

### Post by r4st4m4n on 2008-04-04
Thanks a lot JamesGu.

I'm using fedora 8 and I was pulling my hairs for 2 days to install the Broadcom BCM4310 Wireless card on my Compaq V3759TU when I came across your post.

I cleaned up my previous attempts with ndiswrapper and fwcutter (b43, b43xx, ...) like that:

```

sudo rm /lib/firmware/bcm43*
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils
```

Then followed the instrcutions on the Dell website you posted with the driver you pointed and everything is now working :D

I think in my case the problem was the drivers. I probably was not using the good one as it installed properly with ndiswrapper but it didn't detect my wifi card.

You rock man :guitar:

---

### Post by Nathan.Flow on 2008-04-11
> **JamesGu said:**
> I have the exact same card on my Dell Vostro 1500 and finally got it working. For reference, here's my lspci:

```
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```

And lshw -C network:

```
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:48:56:2d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,09/20/2007, 4.170. ip=192.168.1.41 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

I followed the instructions from dell, here:

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Using the driver from here:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=12&l=en&s=bsdv&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=4&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&cs=12&l=en&s=bsdv&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=4&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819)

(Direct link: [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) )

When you unzip this, you'll have a DRIVER_US directory which contains the right file to use.. (bcmwl5.inf).

Hope this helps!



I have a DV2710us, and have an another laptop with a brodcom card that works just fine( the other laptop) how ever the "Wireless" part of the Wireless network card is not detected 

the out put of my sudo lshw -C is :

the network "Ethernet type" card
*-network
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: a2
       serial: 92:6c:fe:d3:16:00
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: iomemory:fc488000-fc488fff ioport:30f8-30ff iomemory:fc489c00-fc489cff iomemory:fc489800-fc48980f irq:23
 
And what I hope is the Wireless Card
 *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:fc000000-fc003fff irq:10

thanks for any help

---

### Post by demagu on 2008-05-28
JamesGu you are the boss here :)

My DELL XPS M1530 after a week of messing around with wireless (Broadcom 4310 rev 1) finally has a new beatifull connection :)
Thanks!

---

### Post by manij on 2008-05-30
James Gu,

you the Man!

worked like a charm!

Thanks
Mani

---

### Post by mpatria on 2008-06-06
Dear JamesGu
I follow your all tips, for my Acer Aspire 2920Z with ubuntu HH, no error report as I installed. Unfortunatelly, got it no working. For reference, here's my lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


lshw:

 *-network UNCLAIMED
                description: Network controller
                product: BCM4310 USB Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0


mpatria@mpatria-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:2c:90:ea  
          inet addr:152.118.164.128  Bcast:152.118.164.255  Mask:255.255.255.0
          inet6 addr: 2001:e00:f00c:347:21d:72ff:fe2c:90ea/64 Scope:Global
          inet6 addr: fe80::21d:72ff:fe2c:90ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1686518 (1.6 MB)  TX bytes:291855 (285.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77700 (75.8 KB)  TX bytes:77700 (75.8 KB)

thank you for you (or anyone) help

mpatria

---

