---
title: "wireless internet problem"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by dorthedor on 2011-01-03
When i installed wine i could connect wireless and connect to internet.
Then i installed the updates.
A day after i installed updates i could not connect to internet but i could connect wireless to router.
After i removed the wpa/wpa2 security i could connect both wireless and internet.
But now the router i open for anyone who wants to connect to internet(like neighbors)
What can i do?

(When i ping [www.google.com](www.google.com) or the router's ip it won't ping with the wpa/wpa2 protection)

---

### Post by TeoBigusGeekus on 2011-01-03
What's your wireless adapter?
```
lshw | grep net
```

---

### Post by dorthedor on 2011-01-03
Gia sou file :)

Thats what comes up:
        *-network
             description: Ethernet interface
             capabilities: pm bus_master cap_list rom ethernet physical
  *-network
       capabilities: ethernet physical wireless

---

### Post by TeoBigusGeekus on 2011-01-03
Geia sou kai sena.
Post us the output of 
```
lspci
```

---

### Post by dorthedor on 2011-01-03
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0d.0 Ethernet controller: 3Com Corporation 3CSOHO100B-TX 910-A01 [tulip] (rev 31)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

(I do these tests while i am connected to router without wpa/wpa2 protection, i dont know if that makes any difference)

---

### Post by TeoBigusGeekus on 2011-01-03
Do you use a usb dongle for your wireless connection?
If so, post us the output of
```
lsusb
```
as well.

---

### Post by dorthedor on 2011-01-03
I use a usb adapter to connect wireless.

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 045e:0750 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Bucky Ball on 2011-01-03
Must be a dongle as no network controller in that output. That or an interweb miracle! ;)

---

### Post by Bucky Ball on 2011-01-03
Try post #2 fix from chilli555 here:

[http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883)

---

### Post by TeoBigusGeekus on 2011-01-03
Hmm...
Have you seen these threads?
[http://ubuntuforums.org/showthread.php?t=1353044]("http://ubuntuforums.org/showthread.php?t=1353044")
[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")

---

### Post by dorthedor on 2011-01-03
wait, i will check them

---

### Post by Bucky Ball on 2011-01-03
This. Try post #2 fix from chilli555 here:

[http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883)

---

