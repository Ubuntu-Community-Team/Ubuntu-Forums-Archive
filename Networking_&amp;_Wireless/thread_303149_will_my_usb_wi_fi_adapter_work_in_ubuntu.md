---
title: "will my usb wi fi adapter work in ubuntu"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by THEBIGEYE on 2006-11-19
just a quick question.
will my D-LINK airplus G DWL-G122 wireless usb adaptor work in ubuntu? Or is there any drivers avalible sorry to sound naive im new to ubuntu 
cheers

---

### Post by theratster on 2006-11-19
I have exactly the same DLink wireless-USB adapter, and it works great.

In ubuntu 6.06 (the old version) you need a hack to make the networking thing work correctly (search it under my ID in the forums, its there), but under the new one, Ubuntu 6.10, it works great out of the box!

---

### Post by FrodoB on 2006-11-21
What is the output of lsusb?

---

### Post by THEBIGEYE on 2006-11-21
whats is lsusb and how do i find this out sorry im new

---

### Post by FrodoB on 2006-11-21
Go to the Applications Menu in the upper left hand corner of the screen and then select Accessories and then Terminal.

One you have a terminal prompt enter:

lsusb

The output should look something like this:

```

Bus 005 Device 004: ID 0ace:1215 ZyDAS
Bus 005 Device 002: ID 1058:0901 Western Digital Technologies, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

What does yours show?

---

### Post by THEBIGEYE on 2006-11-21
after lsusb i get this


ubuntu@ubuntu:~$ sudo lsusb
Bus 002 Device 009: ID 043d:007b Lexmark International, Inc.
Bus 002 Device 008: ID 043d:007c Lexmark International, Inc.
Bus 002 Device 007: ID 07cf:1001 Casio Computer Co., Ltd QV-8000SX/5700/3000EX Digicam
Bus 002 Device 006: ID 0c45:608f Microdia
Bus 002 Device 005: ID 07d1:3c03 D-Link System
Bus 002 Device 004: ID 043d:007a Lexmark International, Inc.
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard ReceiverBus 001 Device 001: ID 0000:0000
ubuntu@ubuntu:~$

---

### Post by FrodoB on 2006-11-21
Ok, you need to carefully follow this document that covers devices using the rt73 driver:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29)

Good luck.

---

### Post by THEBIGEYE on 2006-11-21
cheers

---

### Post by THEBIGEYE on 2006-11-21
hello me again in that exelent set of instructions u sent me i get up to the part where i have to dled and install the driver the doc takes it im dling it from site i have to dled it thru win and save onto external drive boot in ubuntu how do i locate on ubuntu desktop cheers again people

---

### Post by FrodoB on 2006-11-21
The easiest way is if you have a usb memory sticky like a JumpDriver or Sandisk device.  Copy you data to it in Windows and then reboot into Ubuntu and put the device in and is should appear on the desktop.

---

### Post by THEBIGEYE on 2006-11-21
sorry dont know linux how do i route the path to the file after it on external device or desktop

---

### Post by FrodoB on 2006-11-21
Once you have the USB Memory stick in and can see it, using your mouse pointer select the "Places" menu and the click on "Home Folder" put the files in there.  When you open a terminal and do an "ls" command you will see them all there.

---

### Post by THEBIGEYE on 2006-11-21
back again i can get to step 4 of the instructions but it wont let me change the permissions to -r 775 any ideas?

---

### Post by FrodoB on 2006-11-21
Capital R:

chmod -R 775 *

---

### Post by THEBIGEYE on 2006-11-21
still no joy heres what my terminal says
ubuntu@ubuntu:~$ tar xvzf RT73_Linux_STA_Drv1.0.3.6.tar.gz
RT73_Linux_STA_Drv1.0.3.6/
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/defconfig
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/README
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/driver_ralink.h
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/wpa_supplicant_example.conf
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/drivers.c
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/Makefile
RT73_Linux_STA_Drv1.0.3.6/WPA_Supplicant/driver_ralink.c
RT73_Linux_STA_Drv1.0.3.6/Module/
RT73_Linux_STA_Drv1.0.3.6/Module/md5.h
RT73_Linux_STA_Drv1.0.3.6/Module/rt73.h
RT73_Linux_STA_Drv1.0.3.6/Module/load
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_def.h
RT73_Linux_STA_Drv1.0.3.6/Module/rtusb_data.c
RT73_Linux_STA_Drv1.0.3.6/Module/rtusb_io.c
RT73_Linux_STA_Drv1.0.3.6/Module/rt73sta.dat
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_info.c
RT73_Linux_STA_Drv1.0.3.6/Module/license
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_wep.c
RT73_Linux_STA_Drv1.0.3.6/Module/auth.c
RT73_Linux_STA_Drv1.0.3.6/Module/README
RT73_Linux_STA_Drv1.0.3.6/Module/mlme.c
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c
RT73_Linux_STA_Drv1.0.3.6/Module/assoc.c
RT73_Linux_STA_Drv1.0.3.6/Module/Makefile.4
RT73_Linux_STA_Drv1.0.3.6/Module/md5.c
RT73_Linux_STA_Drv1.0.3.6/Module/connect.c
RT73_Linux_STA_Drv1.0.3.6/Module/ReleaseNote
RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h
RT73_Linux_STA_Drv1.0.3.6/Module/wpa.h
RT73_Linux_STA_Drv1.0.3.6/Module/auth_rsp.c
RT73_Linux_STA_Drv1.0.3.6/Module/config.mk
RT73_Linux_STA_Drv1.0.3.6/Module/mlme.h
RT73_Linux_STA_Drv1.0.3.6/Module/wpa.c
RT73_Linux_STA_Drv1.0.3.6/Module/Makefile.6
RT73_Linux_STA_Drv1.0.3.6/Module/iwpriv_usage.txt
RT73_Linux_STA_Drv1.0.3.6/Module/Makefile
RT73_Linux_STA_Drv1.0.3.6/Module/ifcfg-rausb0
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_type.h
RT73_Linux_STA_Drv1.0.3.6/Module/unload
RT73_Linux_STA_Drv1.0.3.6/Module/sanity.c
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_init.c
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h
RT73_Linux_STA_Drv1.0.3.6/Module/rtusb_bulk.c
RT73_Linux_STA_Drv1.0.3.6/Module/oid.h
RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_tkip.c
RT73_Linux_STA_Drv1.0.3.6/Module/rt73.bin
RT73_Linux_STA_Drv1.0.3.6/Module/sync.c
RT73_Linux_STA_Drv1.0.3.6/Module/Configure
tar: RT73_Linux_STA_Drv1.0.3.6: implausibly old time stamp 1970-01-01 00:00:00
ubuntu@ubuntu:~$ cd RT73_Linux_STA_Drv1.0.3.6/Module
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ chmod -R 775
chmod: missing operand after `775'
Try `chmod --help' for more information.
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$

tryed chmod help no joy 
should i give this up as a bad joke lol

---

### Post by FrodoB on 2006-11-21
You are missing the * at the end.

---

### Post by THEBIGEYE on 2006-11-22
HELP!!! now it wont recognize the make commands
ubuntu@ubuntu:~$ cd RT73_Linux_STA_Drv1.0.3.6/Module
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ chmod -R 775 *
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ fromdos *
bash: fromdos: command not found
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ cp Makefile.6 Makefile
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ gedit rtmp_def.h
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make clean
bash: make: command not found
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make clean
bash: make: command not found
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
bash: make: command not found
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make install
sudo: make: command not found
ubuntu@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$

---

### Post by FrodoB on 2006-11-22
I think you need to work you way back from the beginning. I can see that you do not have fromdos installed for instance.  Just go through each step on line at a time.

If you just want to get make open a new terminal windows and just type make by itself and you should get a message like this:

make: *** No targets specified and no makefile found.  Stop.


That will tell you that make is OK and you have done something else wrong.

---

