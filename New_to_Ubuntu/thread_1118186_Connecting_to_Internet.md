---
title: "Connecting to Internet"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Zickleinmorder on 2009-04-06
Complete and utter ubuntu n00b here.

Just recently procured a PC running ubuntu (specifically v.8.04, codename: hardy).

I'm unable to connect to the internet, whether it's to download updates or simple browsing. When I plug a LAN cord in, it says that it's requesting an address, but then just goes dark.

Thanks in advance for any help.

---

### Post by ameermawia on 2009-04-06
hi! bro,
why dont you just check out your network setting .just right click over the network ikon on your tool bar and choose edit connection ,then select a type of connection or add one and then just edit it's settings by first cheking the method to be manual.settings to be edited ip address ,netmask ,getway,dns server .....
hope it will help you.
with thanks.

---

### Post by Zickleinmorder on 2009-04-06
I know absolutely nothing about my connection, when it comes to that. I was also under the impression that Ubuntu automatically reads all of that when you connect it up.

---

### Post by Zickleinmorder on 2009-04-06
Alright, so I upgraded to 2.10, still the same problem.

---

### Post by RedSingularity on 2009-04-06
Does a windows system work if you plug it in?  I mean ubuntu is supposed to set up the Internet once the cable is plugged in.

Anything wrong with your ethernet port?

---

### Post by Zickleinmorder on 2009-04-07
When a PC running windows is plugged into the modem, it works fine. Great connection. It just doesn't work with the machine running Ubuntu.
I don't think that there's anything wrong with the ethernet port, as when I plug the cable in it says that it's requesting an address but then gives up after a short while.

---

### Post by RedSingularity on 2009-04-07
Do you have any type of encryption enabled?

---

### Post by killbot on 2009-04-07
hey guys. Total newb here as well so some of the terminology might fly over my head, but I am having a similar problem. Just installed Ubuntu today and can't seem to connect. I did the whole add a network thing. Entered the details and it just said something like "network is disconnected". Didn't see a connect option or anything like that. What am I screwing up?

---

### Post by RedSingularity on 2009-04-07
You using ethernet as well?  You shouldnt need to configure anything.  Once the cable is plugged in it should connect automatically.

---

### Post by killbot on 2009-04-07
> **Shadow121 said:**
> You using ethernet as well?  You shouldnt need to configure anything.  Once the cable is plugged in it should connect automatically.

no i am sorry. Should have been specific, I have a wireless connection.

---

### Post by RedSingularity on 2009-04-07
Ok both of you enter "lspci" and "ifconfig" into the terminal and post the output.

---

### Post by RedSingularity on 2009-04-07
Zickleinmorder, after doing some research it sounds like the ethernet port on your ubuntu PC is bad.

---

### Post by killbot on 2009-04-07
> **Shadow121 said:**
> Ok both of you enter "lspci" and "ifconfig" into the terminal and post the output.

sorry but what do you mean by terminal?

---

### Post by killbot on 2009-04-07
> **killbot said:**
> sorry but what do you mean by terminal?

nevermind, got it.

---

### Post by ranch hand on 2009-04-07
Go to Applications -> Accessories -> Terminal

This is the dreaded command line tool.

lspci will list all of your pci stuff (sound, video, winmodem, ethernet, etc).

ifconfig will give the details of your  ethernet hardware and its configuration.

These will give information that will help diagnos your problems.  It is also a good demonstration of how much information you can get from a linux box compared to some other OSs.

I am of no use to you as I do not use wireless.  I just got this box to town where there is DSL and plugged it in and am downloading some more linux OSs to play with.

---

### Post by killbot on 2009-04-07
ted@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:f9:41:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

ted@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by RedSingularity on 2009-04-07
Go to System > Administration > Synaptic Package Manager

Then search for BCM43-fwcutter and install it (right click, and select Mark for installation. then press apply).

During installation, it will ask to fetch the appropriate drivers. Allow it to fetch the drivers.

After the installation is complete, go to System > Administration > Network. Then go to wireless properties and select your wireless network.

---

### Post by Zickleinmorder on 2009-04-07
> **Shadow121 said:**
> Zickleinmorder, after doing some research it sounds like the ethernet port on your ubuntu PC is bad.

Thanks for looking into it.

This person has the same problem as me, it sounds like. Same ISP as well. I'll follow along with it and see where it goes.

[http://ubuntuforums.org/showthread.php?t=1119066](http://ubuntuforums.org/showthread.php?t=1119066)



If it ends up that I do have a bad ethernet port, I assume that getting a wireless card would remedy the problem? Or do I need to have an internet connection in order to get drivers for it?

---

### Post by RedSingularity on 2009-04-07
If your are using a desktop why not buy a replacement PCI Ethernet plug.  Its much cheaper than a wireless card.  And yes most likely you will need internet for the driver download with a wireless card.

---

### Post by Swallace23 on 2009-04-07
I'm having problems as well. I just installed ubuntu a few days ago and both of my integrated Ethernet ports are not working. I plunged in a old card I had lying around and it worked fine. my terminal output is:

scot@Home:~$ lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

eth0      Link encap:Ethernet  HWaddr 00:50:8d:91:37:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:91:37:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:50:bf:9c:3b:04  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe9c:3b04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61270994 (61.2 MB)  TX bytes:2442912 (2.4 MB)
          Interrupt:21 Base address:0xce00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11439 (11.4 KB)  TX bytes:11439 (11.4 KB)

Any help would be awesome. Although I have it working the network card Im using was puled out of a computer that had an original Pentium that come out before they even started using cooling fans. I do know that both of the other ports work fine. I used them to download ubuntu.

---

### Post by killbot on 2009-04-08
> **Shadow121 said:**
>  And yes most likely you will need internet for the driver download with a wireless card.

Bummer, I keep switching back and forth to post here. Didn't see BCM43-fwcutter in the list. Where can I manually dl the drivers? I can just throw them on the jump drive or something. or does it not work that way. :D Thanks for your patience.

---

### Post by RedSingularity on 2009-04-08
Killbot, by any chance did you look under System>Administration>Hardware Drivers?  Sometimes the driver you need is in there.  

Oh and can you hook up a wireless connection to your Ubuntu computer or no?

---

### Post by killbot on 2009-04-08
> **Shadow121 said:**
> Killbot, by any chance did you look under System>Administration>Hardware Drivers?  Sometimes the driver you need is in there.  

Oh and can you hook up a wireless connection to your Ubuntu computer or no?

Well, I get a connection for windows on the same computer, but Ubuntu doesn't connect.

Also it wasn't in Hardware Drivers either. Could i download it on windows, put it to a jump drive, and install it on Ubuntu?

---

### Post by achase79 on 2009-04-08
If your wired ethernet uses the Realtek chipset, then it may not work for that.  Realtek is sometimes a shot in the dark for compatibility with Ubuntu.

---

### Post by RedSingularity on 2009-04-08
Oh im sorry i meant to say can you hook up a WIRED connection to your ubuntu computer?

---

### Post by ameermawia on 2009-04-08
if you have dual boot and ur net is working fine on the window then just copy the network setting from the window.There must be some ip your internet service provider may have provided to you which you can see in window in internet properties.you can just note those setting and fill copy them in ubuntu network setting.this the same way it work for me.
with thanks!

---

### Post by parth.s on 2009-07-02
hey ppl im having similar type of problems..im using ubuntu jaunty..in dual boot with windows xp.
I use my internet connection is through a LAN...and i have to connect to the internet using a username and password
Now in network tools my ethernet card is listed in "network devices" but how do i select it....
also i read about adding the details like ip address, dns etc...But im using Dhcp...

Im stuck plzz guide me ...ive even taken some screenshots

---

### Post by RedSingularity on 2009-07-02
Does network manager connect to the network at all?

---

### Post by parth.s on 2009-07-03
Yes It does connect to the network automatically...the name of the connection by default is Auto eth0...But then what...where do i put in the username and password that i use to connect to internet

---

### Post by RedSingularity on 2009-07-03
Look [here](http://aswinatgec.wordpress.com/2008/08/30/connect-to-internet-in-ubuntu-804-a-simple-guide-to-windows-users/).

---

