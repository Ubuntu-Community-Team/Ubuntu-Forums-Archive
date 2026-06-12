---
title: "Ethernet is disappears then reappears"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by erikcw on 2006-09-14
Hi everyone,

I just switched from XP to Dapper 2 weeks ago, and so far I've been loving it!

I do have a problem though, my Ethernet card (eth0) only works about half the time.

I leave my PC on 24/7.  But if I reboot, eth0 disappears (ubuntu doesn't seem to detect it).  When this happens, I just reboot and it shows up.

So basically every other time I boot my machine, eth0 isn't available.

Does anyone know what is causing this?  Also, is there a command I can run in the terminal to "re-detect" the hardware or activate the card?

Thanks!

---

### Post by tbonius on 2006-09-14
What module is loading for this card?  What typ e of card is it?  It sounds like either the driver or the card itself might be faulty.  Make sure the ethernet card is well seated.  Change PCI slots if you need to.  If it is integrated.. try resetting the BIOS.

T

---

### Post by erikcw on 2006-09-14
It's an integrated card.  This is the first time I've had trouble with it.

> 
erik@turbo:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 81)
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 81)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon X600(RV380)
0000:02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
0000:02:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
0000:02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


Is that the module information you need?  The card is the Intel 82801g.  If not, can you tell me what command to run to find it?

Also - lspci is detecting my other ethernet card - the Marvell Tech Group Wireless - but I have no access to that one - ever...  Any tips on making that one work as well would be greatly appreciated!

Thanks!

---

### Post by tbonius on 2006-09-14
I just see one card here:

0000:02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

I dont see another one.  Looks like its detected just fine.  Like I asked before.. is the other ethernet adapter onboard the motherboard.. and if so what brand/model is the motherboard.  What brand/model is the computer?

T

---

### Post by erikcw on 2006-09-14
The other ethernet controller is:
0000:02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

It's an onboard card, not pci.  The computer is an "HP Media Center PC m7277c".

It's the intel controller (eth0) that shows up sometimes, and disappears other times.  Right now it is working (which is how I'm posting this message).

The Marvell Technology Group is a Wirless PCI card.  It shows up in lspci, but it isn't listed in "System => Administration => Networking".

Hope this helps.

Erik

---

### Post by Nano on 2006-09-15
Looks like the problem I'm experiencing since yesterday. I never had this problem before but since yesterday I can't connect to my server and it works again when I restart it.
I didn't connect it to monitor/keyboard yet so I'm not sure about what's going on.

---

### Post by erikcw on 2006-09-24
Hey everyone - an update...

I finally have Dapper working with my WLAN card.  (The Marvell Tech Group from my lspci).

For the sake of anyone else in my boat, here is what I did.

I followed this HowTo:
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

I ended up having to use ndiswrapper to get my card working.  Now I have wlan0 up and running!

NOTE:  It doesn't mention this in the HowTo, but when I restarted my computer, it froze at "configuring network devices", after letting it sit for 30 minutes, I did a hard reboot and this time it started right up!



I'm still looking for a solution to my eth0 not being detected when I boot up sometimes.  Is there a command that I can run when this happens to make the kernel redetect my hardware - or load the kernel module or something?

---

