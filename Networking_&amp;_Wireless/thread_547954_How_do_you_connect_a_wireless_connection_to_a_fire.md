---
title: "How do you connect a wireless connection to a firewalled network modem in Ubuntu?"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by darktremor on 2007-09-10
Sorry to ask what may be a stupid question, but I'm new to Ubuntu and can't find the answer to this anywhere else online.

How do you connect a computer with a wireless connection to a small wireless network connecting to a cable modem with a firewall?  I can't access the internet with that computer by wire: it's impossible to hook up to the router by wire (the distance is too far and the router is on a different floor), so I have no internet access there at all and therefore cannot use ndiswrapper to get the required wireless driver.  I do have access to the internet on other computers in the house, but they all run some variant of windows (although they do have CD burners, so I can transport software from the internet to my Ubuntu machine).  It is a dual-boot machine, running Windows XP and Ubuntu - is there some way to get the drivers from the windows boot?  I have the passwords for the firewall and all of the information to access it, but it seems to require a special configuration utility that is built only for windows (seeing as the firewall is part of the router), and I can't change it.  Is there any way to get myself connected?  

The router is a D-Link DI-614+ and the firewall is built into it, it connects to the internet using a Rogers cable connection, and the wireless card is also a D-Link (designed to go with that wireless router).  Any ideas?

---

### Post by darktremor on 2007-09-10
Does no one have any solutions to this problem?

---

### Post by jrfarrelly on 2007-09-10
How about a Cisco wireless network?

---

### Post by darktremor on 2007-09-11
It would probably work, but I can't change the network.  I'm connecting to a network already installed by someone else.  Even if I did change the network for a personal use wireless network (which I can't afford), I'd have a lot of signal conflicts with the network already in place.  So I need to be able to use the specific network stated above.

---

### Post by noob12 on 2007-09-12
Well I looked up the information for the DI-614+ and it looks like a normal wireless router.  The access point is logically inside the firewall.  You should just need to install the normal wireless drivers and connect to it using an access key.

Do you have your wireless device setup on Ubuntu already?  If not, you will need to set that up first.
Is there anywhere where you can connect up wired in order to post diagnostics from your machine and download any drivers that might be needed?  

If not, you will probably end up needing at least a jump drive to transfer things to and from the box until it is setup on the network.

Also, it might be possible to determine the type of wireless device you have if you can at least provide the precise model number and revision of the D-link card that you have on your Ubuntu box.

---

### Post by darktremor on 2007-09-12
Yep.  I have a DWL-G510 AirPlus G Wireless G PCI Adapter network card on the computer.

I should've posted that initially; I just assumed the router would have a standard adapter.  Thanks.

---

### Post by noob12 on 2007-09-12
Well different revisions of this card have different chipsets.  The chipset will determine which driver you need.  To determine your chipset, you need to run 
```

lspci -nn

```
on your box and post the output.

---

### Post by darktremor on 2007-09-13
My chipset is D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
However, when I used the lspci command in terminal, it didn't show.  Everything else showed, but that wasn't in there.  I know that's the right chipset, and that I have the right driver, because I have it running perfectly in Windows on the same computer right now (like I said, I have an XP/Ubuntu dual-boot, and I made the Windows internet work).  I simply copied the driver files (including the .inf) right out of the windows folder they run out of.

The issue I'm now having with ndiswrapper is that when I punch:
sudo modprobe ndiswrapper
into the terminal to get ndiswrapper to actually connect, nothing happens.  Then, when I check the module folder (/lib/modules/[*version I can't remember*]/kernel/drivers/net/), there is no folder for ndiswrapper, which should be there.  Re-installing ndiswrapper and retracing the steps did nothing.  The ndisgtk utility actually let me install the driver, but it claimed that the hardware wasn't present (I know it is, Windows ran it just fine).  Upon rebooting the system at that point (which I heard helps), the ndisgtk utility wouldn't even run.

The odd thing is, Ubuntu is actually able to find my network, and lets me enter the key and try to connect to it, and always had before I even tried ndiswrapper.  However, it doesn't actually connect, it simply tries for a while, then asks again for the network information, then tries again, then asks again, and so on.  I know everything inputted is correct, as it's all copied and pasted directly from a text file I made to paste the settings into Windows.  Any ideas?

---

### Post by noob12 on 2007-09-13
What you provided is the model of the card, but these cards tend to have chipsets from a smaller set of actual chip manufacturers.  It often won't be listed with the card manufacturer's name at all.  In your lspci output you will probably see two things listed with the word Ethernet in them.  One of them will have probably have the word Wireless or 802.11 in it.  Post that line.  If in doubt post both lines or all lines.  At very least post the number of the form XXXX:XXXX in the first column for those two devices.  

Based on what you said you probably have the following chipset:

Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

Look in your lspci output and see if you see something like this so we can confirm before proceeding down this path.  Please post exactly what you do find.

You will probably need to use a USB jump drive and another machine (or dual booting your Ubuntu host) to download and transfer files to and fro until you have the connection set up.

For that chipset you may be able to use the drivers in the restricted modules package, but you may need to download more recent madwifi drivers. I wouldn't start with ndiswrapper, but that might be a fallback.

ADDED:  Can you also please say what release of Ubuntu you are running and what the output of **uname -r** says.

---

### Post by darktremor on 2007-09-13
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

There's my lspci output.  You're right.  It was the Atheros driver.  Thanks.  I'll try ndiswrapping that one.  Or do you have any other suggestions for it?

Oh, and my ubuntu release is Feisty fawn 7.04

uname -r output is:
2.6.20-15-generic

Hope that helps solve it. : )

---

### Post by noob12 on 2007-09-13
I believe there is support for the AR5005G in the restricted modules package that comes with Ubuntu.  You just need to download (can download the package and transfer using your USB) and/or enable that in your system.

To use the restricted modules package, first see if you have it installed.  Type
```

dpkg-query -s linux-restricted-modules-2.6.20-15-generic

```
and see if the Status line says "install ok installed".  If so you just need to go to System | Administration | Restricted Drivers Manager and enable the madwifi / Atheros drivers.

If you don't have those, you will need to download the package from this page:
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-generic](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-generic)
When you download the package from there you'll get a **linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb** file.
Transfer that to the ubuntu box and install it using **sudo dpkg --install linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb**
After that you can enable the driver using System | Administration | Restricted Drivers Manager.

Alternatively, you can follow a HOWTO to build more recent madwifi drivers.  Here is a pointer to one HOWTO  [http://ubuntuforums.org/showthread.php?t=485579](http://ubuntuforums.org/showthread.php?t=485579)  for that.

I haven't used an Atheros card before, so I'm not the best guide in these waters.  The contributors on that HOWTO thread probably can help you through whatever you need.

---

### Post by darktremor on 2007-09-13
It's connected: I'm writing to you from Ubuntu right now.  Thanks very much for all your help, I really appreciated it.  : ) : )

---

### Post by noob12 on 2007-09-13
Great!

---

