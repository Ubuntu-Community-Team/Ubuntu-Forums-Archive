---
title: "Connecting to a wireless network"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by zlashed on 2007-08-27
I'm new to ubuntu (i have feisty fawn) and im having trouble connecting to my wireless network. i have an hp pavillion media center tv pc with intel processor.  i am dual booting Xp and Ubuntu. When i start ubuntu, i do not have a wireless connection. and i click on the connection icon and my only choices are wired connection and modem. i am posting this on xp due to the fact that i cant get internet on ubuntu. my computer has built in  wireless lan and an antenna that accept the signal. but i cant seem to connect to my network on ubuntu. if you have any ideas please tell me.

More Computer Specs

Media Center Edition 
Version 2002
Service Pack 2

Intel(R) Core(TM)2 CPU

---

### Post by k0maru on 2007-08-27
Hi. Could you let us know what your wireless card is?
If you're not sure, one easy way is to run:

sudo lspci

in a terminal - and paste those results.

// maru

---

### Post by zlashed on 2007-08-27
thanks k0maru, here are the results

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 LE (rev a1)
03:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:03.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
03:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem

does this help you come up with a solution? if you know of any more help or info, please tell me, thanks.

---

### Post by ryanawall on 2007-08-27
Hi,
[http://ubuntuforums.org/showthread.php?t=75451]("http://ubuntuforums.org/showthread.php?t=75451")
says your card is automaticly supported and that 'You only need to rebuild this module if you have recompiled the kernel'. Follow the guide if you have changed your kernel version. If not 'Configure your new ath0: under System->Administration->Networking'. If that doesn't work you may have these problems: [http://madwifi.org/ticket/808]("http://madwifi.org/ticket/808").

By the way your card is an Atheros AR5006x. I am kind of a noob when it comes to Linux in general, but hopefully this will get you somewhere.

---

### Post by zlashed on 2007-08-28
ryanawall, i tried that, but nothing changed, and i couldn't configure anything. do you need an internet connection for that to work? because like i said, i can only get internet on windows, not ubuntu.

---

### Post by will71110 on 2007-08-28
If you do a iwconfig, what does it give you?

---

### Post by zlashed on 2007-08-28
when i enter iwconfig, i get these results

lo -  no wireless extensions

eth0 - no wireless extensions

so far i have not had any success or any changes. so any more help is appreciated.

---

### Post by k0maru on 2007-08-29
how about the output of
   lsmod | grep ath

?

the output of
   dmesg

maybe useful too - but just give us the parts about the ath_pci module (if it loaded) and wireless.

---

### Post by kevdog on 2007-08-29
See if the madwifi modules will work

To do this, first find your kernel version
uname -r

Then go into synaptic and do a search for "restricted"
Among other things you should find many packages with linux-restriced-modules-(kernel version)

Install the appropriated linux-restricted-modules package that matches your kernel.

Reboot and then let me know what happens.

If nothing works, please post
lshw -C network

Thanks.

---

### Post by zlashed on 2007-08-29
kevdog, i can not install any modules because like i said, i can not connect to the internet on ubuntu. but, i looked and two Linux restricted modules for my kernel version were already installed. there is one that is not though. i can get internet on ubuntu, BUT it involves moving my computer and lots of reconnecting and disconnecting etc. so if you are very sure or think there is a pretty good chance of it working if i install 
that package, then tell me and i will move my computer to install it. thanks. and i decided to input  lshw -C network network anyway, and it gave these results.

*-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       logical name: eth0
       version: 02
       serial: 00:17:31:f0:5f:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.3-2 latency=0 multicast=yes
       resources: iomemory:fdfc0000-fdfdffff iomemory:fdfff000-fdffffff ioport:ff00-ff1f irq:20
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006X 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@03:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: iomemory:fdee0000-fdeeffff irq:18

Thanks a lot and please inform me on any more help.

---

### Post by zlashed on 2007-08-29
thanks k0maru, here are the results for lsmod | grep ath

ath_pci                97312  0 
wlan                  204868  1 ath_pci
ath_hal               192592  1 ath_pci

and for dmesg, i scrolled through a lot of stuff that did not seem relevant, but one thing i saw could help.

wlan: 0.8.4.2 (0.9.3.1)

thanks for your help and tell me if this information helps come up with a solution.

---

### Post by kevdog on 2007-08-29
Based on the output of lshw -C network, there is no driver currently asssociated with your card.

Couple of things to try.

Im not sure if the restricted drivers come on the Ubuntu installation cd by default.  One way to check is do the following
1. Stick ubuntu installation into drive (once you are in ubuntu)
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo apt-cache search linux-restricted

See if anything comes up as far as linux-restricted packages for your kernel version.
If something does appear
5. sudo aptitude install linux-restricted-modules-`uname -r`

Say the above method is a total bust. You could then change strategies and go with ndiswrapper, however this would mean that you would have to have windows xp drivers for you card.

Tell me what you find.

---

### Post by k0maru on 2007-08-29
hey zlashed. i think kevdog has got it right - it hadn't occurred to me that the restricted modules might not be installed, but come to think of it - i had a similar problem with my gf's wireless card - had to connect via wire to download what couldn't be distributed on the cd.

i'm not sure - never used an AtherOS card. if it's a lot of trouble - maybe it's easier to buy a longer cat5 cable? i keep a spare 10m one for such occasions.

---

### Post by zlashed on 2007-08-30
hey kevdog, im starting to think that all of these suggestions do require me to have some sort of internet connection on ubuntu for them to work, because nothing is changing. so i may have to move my computer in order to get a wired connection to set up the wireless. if you have new ideas or info on which ones should work when i do have a connection, please tell me. thanks a lot for your help so far.

---

### Post by kevdog on 2007-08-30
You can get by with the CD for a while, but yes its best if you can have a wired connection.  You could install a lot of the packages as individual .deb files, however you will need a computer with an internet connection to download the deb files and then transfer them to the other computer with a USB stick.

---

### Post by zlashed on 2007-09-01
I can download files on XP and transfer them easily, but i dont know what you mean by "get by with the cd"

---

### Post by zlashed on 2007-09-01
i moved my computer and connecting it with a wire directly, then tried all of the ideas that have been given to me, but still nothing worked. i am still connected with the wire so any other ideas would be appreciated.

---

