---
title: "[SOLVED] Netgear WG311 v1 Wireless Internet Problem"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by dorkdork777 on 2007-01-20
First of all, I'm a complete noob to most of this Linux stuff, the only things I really know how to do are to run apps, and look into folders. That's about it. I'm good with Windows, but this whole Ubuntu stuff is like a whole new confusing universe, filled with scripts and compiling and no being able to access the Internet...

I can access it from Windows and a Mac fine, same goes for my PSP and Wii, but Ubuntu Dapper picks up every network around me except the one I want to connect to, and Edgy fails to find any at all... :( 

I heard that lspci might help, so here's my results - 

```

lspci results (edgy)

00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)

lspci results (dapper)
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)

```

I hope that helped. I'm posting from a Mac sitting next to my PC running the Live CD part of Dapper, so I don't need to restart to download stuff or read more suggestions. Also, my wireless card is Netgear WG311 v1.

TYVM in advance!

EDIT, 26/11/2007 - The problem turned out to be a faulty router, nothing to do with Ubuntu. All is working fine now, and thread marked as solved. :)

---

### Post by dorkdork777 on 2007-01-20
I've now tried connecting to one of the other networks; it still doesn't work. This is getting very annoying - I wanted to upgrade to Ubuntu from Windows back in September, but I didn't because I couldn't connect to the internet!!!

---

### Post by Ashton K. on 2007-01-20
use this:

```
 sudo iwconfig ESSID "ID name" channel "Channel #" enc "Encryption key" 
```

Don't use the " marks obviously. iwoncifg --help list everything it can do.

---

### Post by dorkdork777 on 2007-01-20
My network doesn't have an encryption key, shall I miss out the enc bit? And I think I know what to put into the ESSID part, but the Channel... I have no clue. What do I put in the Channel part?

---

### Post by Ashton K. on 2007-01-20
You can give the channel  bit a miss, same with enc. I happen to know my network is on channel 9, so I tell it so. Although it'll probably resolve channel on its own.

---

### Post by dorkdork777 on 2007-01-21
I tried that, i typed in...

```
sudo iwconfig ESSID parkynet
```

That gave me...

```
Error : unrecognised wireless request "parkynet"
```



Any more help? Please?

---

### Post by dorkdork777 on 2007-01-21
Come on people, I really need this answered. I've now installed Dapper, and it still doesn't work. This is getting annoying.

---

### Post by dorkdork777 on 2007-01-22
I'm sorry to triple post, but I want to make my question available to people in different time zones, who might be able to answer my question. I'd ditch Windows right away if I could get the internet working on Ubuntu, which I've now installed (Dapper).

Edit:
I've got a possible solution - if I hook up my computer via Ethernet to my router, then download a WiFi manager, could that fix the problem?

---

### Post by shane634 on 2007-01-22
Do you have the linux- restricted-modules installed? 

```
uname -r
```

  That will tell you the linux module you are running. 2.6.17-10-386 is mine. See what yours is then open up Synaptic from System-->Administration-->Synaptic package manager and search for linux-restricted-modules and install the one for your architecture what ever it is 386, 686. If you get lost just post here the output of the above command and I can help you further. Good luck.

---

### Post by Steiny1 on 2007-01-22
Hello!

I just installed Edgy last night and I have the same issue, that it..  I am ignorant to Linux and would like to get on line.  If I could make the DVD play back and wireless work, I would get rid of Windows all together.  I have not one bit of know how with the Linux OS and do not understand any of the above.  Would someone out these please take the time to give me a step by step on how to install the wireless card and get it to work?  I have the same card as the other person on this post.  

P.S - When I ask for step by step, I mean it almost literally :)  

I appreciate any help anyone can give..  

Thank You!

---

### Post by dorkdork777 on 2007-01-23
Thanks for the reply! Mine is 2.6.15-26-386. I went into Synaptic, found the linux-restricted module for my number, but it was already installed, it told me. I told it to download and install it again, but of course I don't have internet on Ubuntu. Any more advice?

---

### Post by dorkdork777 on 2007-01-23
Sorry to keep bumping up this thread, but I really need some answers.

---

### Post by dorkdork777 on 2007-01-23
Sorry to make another triple-post, but I found [this]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") webpage, which has details of all fo the working cards for NdisWrapper. My card wan't there, but I found another card with exactly the same chipset as mine - 

```

Card: Netgear WG511T 108Mbps Cardbus adapter (with super G)

    * Chipset: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
    * pciid: 168c:0013
    * Driver: Windows XP driver available on the Netgear CD: netw511.inf + wg511nd5.sys Native
    * Driver: MadWiFi[216]
    * Other:Tested with ndiswrapper 1.2 source compile Note: It's needded 2.6.11.7 kernel with no ACPI support (otherwise kernel risks to crash) 

```

Would it hurt to give me a simplification of these instructions, so I could try it out? Or would it just not work? This is all so very confusing...

---

### Post by nilsw on 2007-01-24
Just got my Netgear WG311T PCMCIA card working on ubunto 6.10 after some struggle. It had wireless contact with my Netgear ADSL firewall router from start but no ip connection. 
I did the following 
1. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) 4.5.2. inspired by the post about disabling ipv6 earlier in this thread. In my case just making the change in Firefox didn't seem to help.
2. I changed the file /etc/network/interfaces. I removed the 2 lines I had concerning wlan0 and added two lines about ath0. Now the four last lines look like this:

map ath0
auto ath0
iface ath0 inet dhcp
wireless-essid XXXXXX

where XXXXXX is the SSID of the router. I do not use encryption, just MAC addresses.

I am not shure why this works and why it didn't work before. The above trouble shooting guide is very good though.

---

### Post by Stochastic on 2007-01-30
> **Ashton K. said:**
> use this:

```
 sudo iwconfig ESSID "ID name" channel "Channel #" enc "Encryption key" 
```

Don't use the " marks obviously. iwoncifg --help list everything it can do.

It should be:
```
 sudo iwconfig ath0 ESSID "ID name" channel "Channel #" enc "Encryption key" 
```
otherwise you're telling iwconfig that ESSID is the device you want to edit and it fails

---

### Post by leclay on 2007-02-15
What is an ESSID?  I'm totally new at this.

Ralph

---

