---
title: "Ubuntu 12.04 won't recognise the Micromax MMX377G USB Modem"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by Akanksha_Saxena on 2013-09-19
Hi all,
I switched to Ubuntu 12.04 (64bit) completely 2 mths back  from Windows. I was using Reliance Netconnect wth Huwai Modem,  configuration for which was pretty much automatic. However, I am having  to switch to another connection BSNL on Micromax MMX377G. It came with  an instruction manual, but i have been unsuccessful in configuring it s  far.

here it goes.

Step 1 : plugging in the dongle with SIM (all unlocked) 
Step 2 : Check the device 
~*$ ls /dev/sr**
/dev/sr0

Now  the manual says if it shows the above output, it means that th software  has been installed before and the asks me to uninstall it with the  following :

*~$ sudo dpkg -r 3g_modem_connect_D301_MMX_amd64.deb*
dpkg: error: you must specify packages by their own names, not by quoting the names of the files they come in.

Step 3 : Mount
*~$ sudo mount /dev/sr0 /mnt*
mount: no medium found on /dev/sr0

So i searched online there were lots of threads on previous models, 

I did the following : 
~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 24ae:1000  
Bus 001 Device 006: ID 1c4f:0003 SiGma Micro HID controller
Bus 001 Device 005: ID 0bc2:3312 Seagate RSS LLC 
_Bus 002 Device 020: ID 2020:4010  _*(I  think this is my new modem - this appears only when the new stick is  connected, once it appeared with the ID 2020:0002, but that stopped happening now.)*
Bus 002 Device 018: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card *(my old trusty Netconnect)*
Bus 002 Device 004: ID 05e3:0722 Genesys Logic, Inc.

I have tried a couple of solutions given online like modeswitch and something that crashed my computer once.

Please could anyone tell me what is the problem here?

---

### Post by pankaj4 on 2013-09-24
Hello,
I think you did not read the manual correctly, the second step mentions a 'sudo dpkg **-i **3g_modem_connect_D301_MMX_amd64.deb" not a '-r'. Also, do make sure the device /dev/sr0 is indeed the USB Modem you want to install if there are more than one listed( if unsure, just remove the device and run ls /dev/sr* again to see which one has disappeared). I have just installed the same on ubuntu12.04, using the exact installation instructions provided with the product, works like a charm.

---

### Post by varunendra on 2013-09-26
> **pankaj4 said:**
> I have just installed the same on ubuntu12.04, using the exact installation instructions provided with the product, works like a charm.
Hello Pankaj !

Could you please confirm the device ID of your modem? Because I just checked on mine, and it seems 2020:4010 (or 2020:0002) is not supported natively, at least not on my system. But then I haven't updated for months, and am still on kernel 3.2.0-36 :P

So if your modem is actually the same, then it is either the installer program, or the latest updates that included the support for it.

> **Akanksha_Saxena said:**
> 
_Bus 002 Device 020: ID 2020:4010  _*(I  think this is my new modem - this appears only when the new stick is  connected, [COLOR="#FF0000"]once it appeared with the ID 2020:0002, but that stopped happening now.[/COLOR])*
That is actually a good sign. It means at least the modeswitching now successfully takes place, and you are probably just one step behind.

Once the modem has changed its mode, all that is left is binding the driver "option" with the device. This can be done on a running system with a command (for testing), or can be configured to happen automatically (to make it permanent if the test succeeds).

**PS:**
Welcome to the forums both of you ! :D

---

### Post by Akanksha_Saxena on 2013-10-08
it doesn't work. tried Pankaj's suggestion.

---

### Post by varunendra on 2013-10-08
> **Akanksha_Saxena said:**
> it doesn't work. tried Pankaj's suggestion.

Please remove the modem, wait for about 10 seconds. Then plug it back in --> wait for about 1 minute --> run the following commands and post back their outputs -
```
lsusb
dmesg | tail -20
lsmod
usb-devices | grep -iA14 -B4 2020
modprobe -c | grep -i 2020.*4010
```

..And, just to see if we can get the drivers located on the modem itself, please try this -
```
sudo sed -i '/^Disable/ s:0:1:' /etc/usb_modeswitch.conf
```
Now unplug --> replug the modem and re-check-
```
lsusb
```
Do you see the ID 2020:0002 device again (or anything other than 4010 with 2020)? If not, reboot and try again. Now? If yes, what does this tell us -
```
ls /dev/sr*
```

**PS:**
The above change to the /etc/usb_modeswitch.conf file will disable the modeswitching so that we can access the storage (virtual cd) part of the modem. To be able to use it as a modem again, you will have to change the value "1" back to "0" with -
```
sudo sed -i '/^Disable/ s:1:0:' /etc/usb_modeswitch.conf
```
However, I suggest you keep it to "1" until we can copy the driver off its storage part. As soon as it is done, change it back to "0" with above command (you can of course also edit it with your GUI text editor, opening it as root).

---

