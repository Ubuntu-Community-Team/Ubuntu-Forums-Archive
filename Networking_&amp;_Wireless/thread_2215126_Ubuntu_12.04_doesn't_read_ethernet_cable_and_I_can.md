---
title: "Ubuntu 12.04 doesn't read ethernet cable and I cannot activate wifi driver"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by michi3 on 2014-04-04
Hi! I have an Hp mini 1000 with XP. I installed Ubuntu 12.04 LTS (32 version) but I don't have wifi. I plugged my netbook to my ethernet cable but it doesn't read it either.
I read another posts to try to fix it by myself but I was unsuccessful. 
I tried the following codes:

[COLOR=#0000cd]rfkill list all

0:hp wifi: wireless LAN
            soft block:no
            hard block:no
1::hp wwan: wireless wan
                 soft block:yes
                 hard block:no

lspci  --nn | grep 0280

lspci:invalid option -- '-'
usage:lspci [<switches>]

[/COLOR]Any help will be greatly appreciated . Thanks:D:popcorn:

---

### Post by chili555 on 2014-04-04
> lspci --nn | grep 0280

lspci:invalid option -- '-'
usage:lspci [<switches>]It is actually:```
lspci -nn | grep 0280
``` Not --nn. Since we're also looking at ethernet, please let us see:```
lspci -nn | grep -e 0280 -e 0200
```Thanks.

---

### Post by michi3 on 2014-04-04
I wrote 
[COLOR=#0000cd]lspci -nn | grep -e 0280 -e 0200

[/COLOR]I got
[COLOR=#0000cd]01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY[14e4:4315](rev01)
[/COLOR]:popcorn:[COLOR=#0000cd]
[/COLOR]

---

### Post by chili555 on 2014-04-04
We see no ethernet yet. Let's widen the search:```
lspci -nn
lsusb
```

---

### Post by michi3 on 2014-04-04
Thanks  Chili for your help:)
I input 
[COLOR=#0000cd]
lspci -nn
[/COLOR] 
and I got this

[COLOR=#0000cd]
s Integrated Graphic Controller[8086:27ae]  (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/9[/COLOR]
[COLOR=#0000cd]40 GML Express Graphic Integrated Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition
Audio Controller [8086:27d8] (rev02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1
[8086:27d0] (rev02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2
[8086:27d2] (rev02)
00:1d.0 USB controller [0c03]: Intel Corporation [/COLOR][COLOR=#0000CD]NM10/ICH7 Family USB UHCI Contr
[/COLOR][COLOR=#0000cd]oller #1 [8086:27c8] (rev02)
[/COLOR][COLOR=#0000CD]00:1d.1 USB controller [0c03]: Intel Corporation [/COLOR][COLOR=#0000CD]NM10/ICH7 Family USB UHCI Contr
[/COLOR][COLOR=#0000CD]oller #2 [8086:27c9] (rev02)
[/COLOR][COLOR=#0000CD]00:1d.2 USB controller [0c03]: Intel Corporation [/COLOR][COLOR=#0000CD]NM10/ICH7 Family USB UHCI Contr
[/COLOR][COLOR=#0000CD]oller #3 [8086:27ca] (rev02)
[/COLOR][COLOR=#0000CD]00:1d.3 USB controller [0c03]: Intel Corporation [/COLOR][COLOR=#0000CD]NM10/ICH7 Family USB UHCI Contr
[/COLOR][COLOR=#0000CD]oller #4 [8086:27cb] (rev02)
[/COLOR][COLOR=#0000CD]00:1d.7 PCI bridge [0601]: Intel Corporation [/COLOR][COLOR=#0000CD]82801GBM (ICH7-M) LPC Interface Bri
[/COLOR][COLOR=#0000cd]dge [8086:27b9] (rev02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G  (ICH7 Family) IDE Control
ler [8086:27df] (rev02)
00.1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:
27da] (rev02)
01.00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY
[14e4:4315] (rev 01)

[/COLOR]lsusb
[COLOR=#0000cd]
Bus 001 Device 002: ID 10f1:1a08 Importek Internal Webcam
[/COLOR][COLOR=#0000CD]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/COLOR][COLOR=#0000CD]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/COLOR][COLOR=#0000CD]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][COLOR=#0000cd]
[/COLOR][COLOR=#0000CD]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][COLOR=#0000cd]
[/COLOR][COLOR=#0000CD]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][COLOR=#0000cd]

[/COLOR][COLOR=#0000cd][/COLOR]

---

### Post by chili555 on 2014-04-05
We still see no ethernet. Does your device actually have one? Is it defective? Is it enabled in the BIOS? 

Let's fix the wireless without ethernet. Please download this file on any other computer. Transfer it on a USB key or similar and drag and drop it to the desktop. [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb) 

Now we install it:```
cd ~/Desktop
sudo dpkg -i linux*.deb
```Now unload and reload the driver so it sees the shiny new firmware:```
sudo modprobe -r b43 && sudo modprobe b43
```Your wireless should now be working.

---

### Post by michi3 on 2014-04-06
I downloaded the file to my USB. I followed all the steps that you mentioned Chili555 and when I opened network folder suddenly appeared wifi. So it is working right now.
Thanks a lot Chili555:KS:KS:KS

---

### Post by chili555 on 2014-04-06
Awesome! Please use thread tools at the top to mark Solved.

Note to the searchers: this solution is for  Broadcom Corporation BCM4312 802.11b/g LP-PHY
[[COLOR="#FF0000"]14e4:4315[/COLOR]] (rev 01) only. If this isn't your device, please post a new question with your details.

---

