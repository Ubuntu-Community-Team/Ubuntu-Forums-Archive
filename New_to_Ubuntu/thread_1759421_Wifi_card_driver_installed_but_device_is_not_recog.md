---
title: "Wifi card driver installed but device is not recognized"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Tripe46 on 2011-05-15
Hey all, new to the forum, and ubuntu.  I used ndiswrapper to install the drivers for my realtek/filemate wireless card.  Ndiswrapper says that the hardware is present, and I can't figure out what to do next.  I tried adding it to network devices but no luck.

Any help is greatly appreciated.

---

### Post by dcsoldschool53 on 2011-05-15
> **Tripe46 said:**
> Hey all, new to the forum, and ubuntu.  I used ndiswrapper to install the drivers for my realtek/filemate wireless card.  Ndiswrapper says that the hardware is present, and I can't figure out what to do next.  I tried adding it to network devices but no luck.

Any help is greatly appreciated.

When you left click on the network applet what do you see? And, when you right click on it what do you see?

---

### Post by dcsoldschool53 on 2011-05-15
What is the name of your network card?

---

### Post by Tripe46 on 2011-05-15
What is the network applet? Is it the thing at the top right of the screen to the left of the time?

The wireless card is a wintec/filemate pci wireless n card model 3FMPCIMWN-R.

---

### Post by wildmanne39 on 2011-05-15
> **Tripe46 said:**
> What is the network applet? Is it the thing at the top right of the screen to the left of the time?

The wireless card is a wintec/filemate pci wireless n card model 3FMPCIMWN-R.

Hi click on the icon in the top right of the screen that is for your connection and see if it is enabled and the you hace to put in your password or phrase to connect.:)

---

### Post by Tripe46 on 2011-05-15
I currently have a wired connection and there are no other options even though I added a wireless connection.  The same is true when I have the wired connection unplugged

---

### Post by Tripe46 on 2011-05-15
Also when i try to iwconfig wlan0 up it says no such device

---

### Post by dcsoldschool53 on 2011-05-15
try those command```
 sudo lshw -c network
```
```
nm-tool
```Copy and paste you output of the first one only.

---

### Post by dcsoldschool53 on 2011-05-15
The only info I could find out about your card was that Ubuntu had issues with it.:confused:

---

### Post by Tripe46 on 2011-05-16
> **dcsoldschool53 said:**
> try those command```
 sudo lshw -c network
``````
nm-tool
```Copy and paste you output of the first one only.

trip@linux:~$ sudo lshw -c network
[sudo] password for trip: 
  *-network               
       description: Ethernet interface
       product: 88E8050 PCI-E ASF Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 17
       serial: 00:11:11:bc:7e:f4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.13 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fe8fc000-fe8fffff ioport:a800(size=256) memory:fe8c0000-fe8dffff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:b800(size=256) memory:feaff000-feafffff

---

### Post by Tripe46 on 2011-05-16
> **dcsoldschool53 said:**
> The only info I could find out about your card was that Ubuntu had issues with it.:confused:
The more searching I do the more I agree with you.  Can you recommend an inexpensive card that is "plug and play"?

---

### Post by wildmanne39 on 2011-05-16
> **Tripe46 said:**
> The more searching I do the more I agree with you.  Can you recommend an inexpensive card that is "plug and play"?
Hi, those commands do not even show you have a wireless card. Is your card built in? what do you get when you put lspci in a terminal?:D

---

### Post by dcsoldschool53 on 2011-05-16
> **Tripe46 said:**
> The more searching I do the more I agree with you.  Can you recommend an inexpensive card that is "plug and play"?

Sorry it was getting late and I had to get some rest.

Here are two sites that you can goto to search for yourself about what cards are compatible with Ubuntu..

Ubuntu Catalog
[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)

Help Ubuntu card support
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer)

Have a look about and choose what card you think is best for you.

---

### Post by dcsoldschool53 on 2011-05-16
What the```
nm-tool
```command should show, is Information about your:
1.) wired network
2.) wireless network
3.) wireless properties
4.) Wireless Access points

If your card is working right, you would be picking up a signal from your router and anyone who has a signal in your vicinity.

---

### Post by Tripe46 on 2011-05-18
> **wildmanne39 said:**
> Hi, those commands do not even show you have a wireless card. Is your card built in? what do you get when you put lspci in a terminal?:D

Its a PCI wireless card that I installed, and it was working in windows (although I can't check that now because windows won't boot since installing ubuntu :(

trip@linux:~$ lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)
06:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
06:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)

---

### Post by Tripe46 on 2011-05-18
> **dcsoldschool53 said:**
> What the```
nm-tool
```command should show, is Information about your:
1.) wired network
2.) wireless network
3.) wireless properties
4.) Wireless Access points

If your card is working right, you would be picking up a signal from your router and anyone who has a signal in your vicinity.

trip@linux:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:11:11:BC:7E:F4

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.242.0.12


Clearly ubuntu is not even recognizing my wireless card.  I think it may be wiser for me to buy a card that I know will work rather than making myself crazy trying to get the one that I have work.

---

### Post by Tripe46 on 2011-05-18
This is my third attempt at forcing myself to use a Linux machine.  My first two attempts were thwarted by the exact same issue that I'm having, I figured if it was this hard to make my wireless card work that I didn't want to be bothered with the rest.

However now I am feeling more patient and less stubborn about it, so hopefully I can get my self a "plug and play" wireless card and move on to the next thing.

Thanks everyone.

---

### Post by wep940 on 2011-05-18
Actually, it is showing your wireless adapter - it just doesn't know a thing about it right now. The line: 06:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190 is actually the wireless adapter (do a net search on Realtek 8190 and it turns up).
 
I'll be looking for some info on getting this working ubuntu. In the meantime, if you having nothing of importance yet in your ubuntu install, reinstall it and do nothing more. Otherwise, back out ALL of the changes you have made - the driver in ndiswrapper, ndiswrapper itself, any changes to the blacklist, etc., etc., etc., to get back to a known clean status.
 
EDIT:  Forgot to mention - if you use ndiswrapper, be sure to use the GUI'd front end to it ndisgtk.  It takes away a lot of typing and you don't have to touch the command line.  Also, ndiswrapper can use Windows XP drivers *ONLY* (not Windows 7, etc. - they'll show a device but it will never work), and those Windows XP drivers must be of the same architecture as your ubuntu - 32 bit or 64 bit.

---

### Post by Tripe46 on 2011-05-18
> **wep940 said:**
> Actually, it is showing your wireless adapter - it just doesn't know a thing about it right now. The line: 06:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190 is actually the wireless adapter (do a net search on Realtek 8190 and it turns up).
 
I'll be looking for some info on getting this working ubuntu. In the meantime, if you having nothing of importance yet in your ubuntu install, reinstall it and do nothing more. Otherwise, back out ALL of the changes you have made - the driver in ndiswrapper, ndiswrapper itself, any changes to the blacklist, etc., etc., etc., to get back to a known clean status.
 
EDIT:  Forgot to mention - if you use ndiswrapper, be sure to use the GUI'd front end to it ndisgtk.  It takes away a lot of typing and you don't have to touch the command line.  Also, ndiswrapper can use Windows XP drivers *ONLY* (not Windows 7, etc. - they'll show a device but it will never work), and those Windows XP drivers must be of the same architecture as your ubuntu - 32 bit or 64 bit.

Gotcha, I definitely tried to install 7 drivers with ndiswrapper.  I will reinstall ubuntu, thanks!

---

### Post by manns41078 on 2011-05-26
Same exact issue here. I thought maybe the problem would be resolved in Ubuntu 11, but nope. I've got Ubuntu 10.04 installed again due to other instability issues from 11.

At any rate I downloaded what appears to be the source code for the linux drivers from filemate/wintec. But I've no clue how to build the source and install the drivers.  There's instructions in the readme, but they're too vague for a newbie linux user.

So with faith that someone out there would be willing to decipher this instruction file into non-linux speak for me (i.e. what bash commands to enter) I would love to give it a go.

See attached readme.txt or get the full archive source from:
[http://www.wintecind.com/support_center/Downloads/](http://www.wintecind.com/support_center/Downloads/)

Thanks in advance!

---

