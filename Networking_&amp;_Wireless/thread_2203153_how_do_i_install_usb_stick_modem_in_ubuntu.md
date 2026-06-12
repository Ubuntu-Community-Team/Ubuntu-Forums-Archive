---
title: "how do i install usb stick modem in ubuntu??????????????"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Hasan55 on 2014-02-01
hey guys help me plz ..............



how do i install my usb stick in ubuntu 13.04 version ...............

when i used xp then after pluging the usb stick it atomatically begun to install software and installing proccess complete successfully but now i am using ubuntu 13.04 version and i plug in my usb stick but nothing is happing i don't know HOW TO INSTALL  SOFTWARE OF THIS USB STICK IN UBUNTU........................

MY USB STICK MODEL NO.............HUAWEI Mobile Broadband
                                  Model:E 1550
                                  HSDPA USB Stick

---

### Post by vasa1 on 2014-02-01
There are several usb modems that don't work with Ubuntu (or Linux) because the vendor doesn't provide the requisite software.

But in your case, people have got it to work:
[https://wiki.archlinux.org/index.php/Huawei_E1550_3G_modem](https://wiki.archlinux.org/index.php/Huawei_E1550_3G_modem)
[https://bbs.archlinux.org/viewtopic.php?id=172080](https://bbs.archlinux.org/viewtopic.php?id=172080)

Apologies for the archlinux link but I didn't come across ones for Ubuntu.

---

### Post by PotatoHead007 on 2014-02-01
Hi, i am not sure about terminal commands, but you can try installing modem-manager GUI pakage if your network manager does not have the "Enable mobile broadband" option. Also, here might be a helpful link: [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
Post feedback please :)

---

### Post by vasa1 on 2014-02-01
> **PotatoHead007 said:**
> ...Also, here might be a helpful link: [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
Post feedback please :)

+1

Nice link and OP's modem is included but for much older versions of Ubuntu.

---

### Post by 3rdalbum on 2014-02-02
Let's start with the basics. Go to the bar on the top of the screen. There is an icon toward the right side for the Network Manager. Click it, then click on Edit Connections.

Go to the Mobile Broadband tab and click Add. Answer the questions it asks to set up the connection. After that, your connection should work. You can connect or disconnect through the Network Manager menu in the top panel.

---

### Post by varunendra on 2014-02-02
In the direction of technical aspects of the basics, we also need to know if the modem actually 'switches' to modem mode first (only then Network Manager would be able to pick it up).

To check that, please plug-in your modem, wait for about 30 seconds, then open a terminal (Ctrl-Alt-T), and run the following commands -
```
lsusb
dmesg | tail -20
```
Post back the outputs for us so we can see if it changed its mode (from 'Storage' device to 'Modem').

---

### Post by QIII on 2014-02-02
Moved to Networking & Wireless

---

### Post by Hasan55 on 2014-02-02
thanks all of my helpful frinds for your quick reply.................



i had followed VARUNENDRA......................

after opening terminal i commanded..........and then.

ruhul@hasan-G41M-Combo:~$ lsusb
Bus 001 Device 008: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 003 Device 002: ID 0e8f:0022 GreenAsia Inc. 
Bus 004 Device 002: ID 2188:0ae1  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ruhul@hasan-G41M-Combo:~$ dmesg | tail -20
[  453.700237] scsi7 : usb-storage 1-8:1.6
[  454.291384] usbcore: registered new interface driver usbserial
[  454.291824] usbcore: registered new interface driver usbserial_generic
[  454.291918] usbserial: USB Serial support registered for generic
[  454.351509] usbcore: registered new interface driver option
[  454.353133] usbserial: USB Serial support registered for GSM modem (1-port)
[  454.354776] option 1-8:1.0: GSM modem (1-port) converter detected
[  454.355029] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[  454.355096] option 1-8:1.3: GSM modem (1-port) converter detected
[  454.355284] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
[  454.355315] option 1-8:1.4: GSM modem (1-port) converter detected
[  454.355493] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
[  454.700190] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  454.705692] scsi 7:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  454.714166] sr1: scsi-1 drive
[  454.714377] sr 6:0:0:0: Attached scsi CD-ROM sr1
[  454.714520] sr 6:0:0:0: Attached scsi generic sg2 type 5
[  454.714848] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  454.726510] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  517.992075] usb 3-1: USB disconnect, device number 3
ruhul@hasan-G41M-Combo:~$ 




GUYS WHAT NOW SHOULD I COMMAND ......IT DOES NO SENSE TO ME AT ALL.:p

---

### Post by 3rdalbum on 2014-02-02
Can you please confirm that you tried what I suggested?

---

### Post by varunendra on 2014-02-02
> **Hasan55 said:**
> 
[  454.355315] option 1-8:1.4: GSM modem (1-port) converter detected
[  454.355493] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2

Yup, it is indeed switched and detected as a modem. Network Manager should be able to detect it and show you an option "New Mobile Broadband Connection" (or something similar, assuming it is not yet configured for any Mobile Broadband connections) in its drop-down menu. Now comes the part that 3rdalbum suggested. Did you follow that? Please give us details of what happened if you did follow that.

---

### Post by praseodym on 2014-02-02
Please have a look here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by Tom_Walker on 2014-04-05
easy step to install modem in ubuntu,
click [http://www.gedapps.com/2014/04/install-modem-on-ubuntu-using-sakis3g.html](http://www.gedapps.com/2014/04/install-modem-on-ubuntu-using-sakis3g.html)

---

