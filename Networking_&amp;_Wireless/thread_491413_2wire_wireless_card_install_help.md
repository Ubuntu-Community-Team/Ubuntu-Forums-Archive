---
title: "2wire wireless card install help"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by qpalu on 2007-07-03
Hello i am trying to get my wireless working but cannot seem to connect. The 2wire card says its Agere systems based. Found many posts googlin saying i dont need ndiswrapper for 2wire 802.11 cards and that the card is hermes I it should work.  I am unable to access the internet or the homeportal router.  iwconfig displays the following ...

eth0  IEEE 802.11b   ESSID:2wire112  Nickname:"HERMES I"
mode:Managed  Frequency:2,457 GHz Access Point: None
Bit Rate:11 Mb/s  Sensitivity: 1/3
Retry Limit:4 RTS thr:off  Fragment thr:off
Power Management:off
Link Qaulity=0/92 Signal level=134/153 Noise level=134/153
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retires:3 Invalid misc:0 Missed beacon:0


Sry if this is hard to follow was bored found live cd played with it, liked it and instaled it on laptop today so im pretty newbish and every guide i seem to find googling says something different in each one. Will this work ? do i just need to change some settings ? or do i actually need to install ndiswrapper and do it thta way? My laptop dosent have a ethernet jack on it ( ya its old) so wireless is the only way for me to hook it up unless i swap usb connections on homeportal between Ubuntu laptop and the other pc. I dont mind a challenge if someone could just point me in the right direction as far as if the default driver will work or ndiswrapper etc.. im williing to learn just new and confused ! 8( LOL ... Thanx in advance for any advice anyone can provide

---

### Post by limbourg31 on 2007-07-03
eth0 is the ethernet port so if you're doing wireless you would be looking at wlan0 or wmaster0 if you're one Edgy or the specific driver based install for Feisty

---

### Post by qpalu on 2007-07-03
I am using Feisty. . I dont have a ethernet jack on my laptop i am using a external wireless card from 2wire.

---

### Post by Ayuthia on 2007-07-03
Can you post the following:
lspci -nn
lshw -C network

---

### Post by qpalu on 2007-07-03
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 FireWire (IEEE 1394) [0c00]: Sony Corporation CXD3222 i.LINK Controller [104d:8039] (rev 02)
00:09.0 Multimedia audio controller [0401]: Yamaha Corporation YMF-744B [DS-1S Audio Controller] [1073:0010] (rev 02)
00:0a.0 Communication controller [0708]: Rockwell International HCF 56k Data/Fax Modem [127a:2005] (rev 01)
00:0c.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
00:0c.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
01:00.0 VGA compatible controller [0300]: Neomagic Corporation NM2200 [MagicGraph 256AV] [10c8:0005] (rev 20)

                     and lshw -C network ...

*network
       description: Wireless interface
        physical id:3
        logical name:eth0
        serial:00:02:2d:8d:31:5e
        capabilities: ethernet physical wireless
         configuration: broadcast=yes driver=orinoco driversion=0.15 firmware=Lucent/Agere 8.42 multicast=yes

wireless=IEEE 802.11b

Thank you guys for offering help so fast its much appreciated

---

### Post by Ayuthia on 2007-07-03
By any chance, is this a USB device?  If so, can you post lsusb?  I would like to see the device information.

---

### Post by qpalu on 2007-07-03
its a pcmcia card. default one they shipped me with sbc/att install.  it shows up as wireless pc card in the device manager but the device listings is blank vendor and device is unkown status just says status and bus type says pcmcia device type and capabilites say unknown also.  the advanced section for both pc card and wlan interface have values i can post that if it will help

---

### Post by limbourg31 on 2007-07-03
strange, it seems like the drivers aren't working after all because that was how my Linksys was in Edgy

---

### Post by Ayuthia on 2007-07-03
It wouldn't hurt to post it.  It might help someone figure out what needs to be done.  I have looked around and there seems to be some that say that it works out of the box, some say that you need to download drivers, and others say to use madwifi or ndiswrapper.  The only way to figure out which way to go is to figure out which make, model, and version you have.  Usually, the information is found using lspci or lsusb, but I don't see it there.

---

### Post by t4thfavor on 2007-07-04
I know this thread is a few days old, but I think I can help. You need to stop trying to use network manager. Just issue a few commands on the terminal and you will be off

sudo iwconfig eth0 essid "your ssid" key "your web key for the 2wire"

and your off. The hermes is old, and very well supported. Its just that network manager sometimes has a hard time with wep. (Most 2wire's are only wep encrypted)

---

### Post by qpalu on 2007-07-05
Solved!! Thank you guys for all the help and advice. After following t4hflavor's advice the thing fired right up and away i went !! Thanx so much !

---

### Post by shermie on 2007-07-14
I am very new to Ubuntu and am having the same problem. I noticed t4th stated using the terminal. For someone who has no clue (I just installed it yesterday) where to begin could you please go through the steps for me.

thank you

---

