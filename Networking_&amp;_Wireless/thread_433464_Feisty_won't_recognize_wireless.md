---
title: "Feisty won't recognize wireless"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by dislocated on 2007-05-05
I know there are a lot of questions about wireless not working, and I don't want to over post on the issue, but I've looked and looked and can't find an answer to my problem.

Feisty will not recognize my wireless card **at all**. The wifi light does not even light up. It's like the hardware doesn't exist.

Dell Ispiron 6400
Dell wireless 1500 802.11n mini card
I'm using the 64 bit version of Feisty since the 32 bit version wouldn't install for me.

Any help would be greatly appreciated.

---

### Post by Floppyjoe on 2007-05-05
This information was on the Ndiswrapper list site for your card:
> #
Card: Dell Wireless 1500 (802.11draft-n/a/g) WLAN MiniCard

    *
      Chipset: Broadcom BCM4321(?) (rev 01)
    *
      pciid: 14e4:4328
    *
      Driver: [http://ftp.us.dell.com/network/R129083.EXE](http://ftp.us.dell.com/network/R129083.EXE)
    *
      Other: ndiswrapper v1.22-rc1, Ubuntu kernel 2.6.15-26-386


That means someone has got that card working with ndiswrapper before.

---

### Post by Candace on 2007-05-05
Hi dislocated (hopefully not for long  :wink: ),
I know there are a lot of posts here, so I am going to kindly direct you to them. They are very clear and simple, that even a newbie like me could follow them. I installed Ubuntu 7.04 on an HP dv2000 with wireless card Broadcom 1390 WLAN and these things worked for me. 

1. Follow the instructions here: 

[http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505)

2. Then, your blue wifi light should be on, and follow the instructions here:
 
[http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

Hope that helps, now that I have wireless working, I want everyone else to have it too. :) Please note: this doesn't include encryption, for which there is a How To here, which I haven't got working yet. 

3. Encryption: [http://ubuntuforums.org/showthread.php?t=202834&page=40](http://ubuntuforums.org/showthread.php?t=202834&page=40)

---

### Post by dislocated on 2007-05-05
Thanks for trying to help, but I had found and followed those instructions before to no avail. Just for fun, I tried it all again.. same result.

I haven't a clue what is going wrong. The green WiFi light still stays off and when I type:
```
$ sudo ndiswrapper -l
```
I get:
```
bcml5 : invalid driver!
bcmwl5 : driver installed
```
Aslo, 
 ```
sudo iwlist scanning
```gives
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```
eth0 is my cable ethernet.
Here is my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```
Looks to me like the problem is in the last line: "Unknown device"

---

### Post by dislocated on 2007-05-05
If anyone else is having positive results from the method in the above link, this worked for me:

In the beginning, when you are "cleaning things up",...

Instead of cleaning things up with this:
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
```
I used this instead:
```
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils
```
That puts me one step closer to cleaning Window$ off my hard drive for good! :)

---

