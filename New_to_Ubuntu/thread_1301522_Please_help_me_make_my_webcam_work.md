---
title: "Please help me make my webcam work"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by mvalviar on 2009-10-26
I already looked googled for a solution but I can't find any. I have a A4Tech PK-52MF webcam. I doesn't work out of the box but I hope I can get it to work. I hope the following are relevant

```
mvalviar@mumee:~$ uname -a
Linux mumee 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

mvalviar@mumee:~$ lsusb
Bus 001 Device 005: ID 0ac8:0328 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mvalviar@mumee:~$ dmesg
...
[ 3018.542288] usb 1-6: USB disconnect, address 3
[ 3047.212028] usb 1-6: new high speed USB device using ehci_hcd and address 4
[ 3047.446049] usb 1-6: configuration #1 chosen from 1 choice
[ 3047.446907] gspca: probing 0ac8:0328
[ 3047.652229] vc032x: check sensor header 32
[ 3047.655714] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3047.659717] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3047.663464] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3047.667215] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3047.670965] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3047.680715] vc032x: Read Sensor h (0x00) m (0x43) l (0x82)
[ 3047.680963] vc032x: Unknown sensor...
[ 3047.680986] vc032x: probe of 1-6:1.0 failed with error -22
[ 3530.689344] usb 1-6: USB disconnect, address 4
[ 3831.412522] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 3831.658406] usb 1-6: configuration #1 chosen from 1 choice
[ 3831.659120] gspca: probing 0ac8:0328
[ 3831.869981] vc032x: check sensor header 32
[ 3831.873474] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3831.877223] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3831.880974] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3831.884725] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3831.888473] vc032x: Read Sensor h (0x00) m (0x00) l (0x00)
[ 3831.900724] vc032x: Read Sensor h (0x00) m (0x43) l (0x82)
[ 3831.900972] vc032x: Unknown sensor...
[ 3831.900995] vc032x: probe of 1-6:1.0 failed with error -22


```

I already tried easycam but it doesn't work.

---

### Post by mvalviar on 2009-10-26
^^bump^^ Sorry if it's too early. This is really urgent.

---

### Post by MelDJ on 2009-10-26
try another program.. cheese for example

---

### Post by thejranjan on 2009-10-26
sudo apt-get install cheese

Cheese webcam booth is a software that makes you to use ur webcam :p

---

### Post by howefield on 2009-10-26
If it isn't working out of the box, try using your favourite search engine with the ID in the search term, eg 0ac8:0328 ubuntu 

Amongst 269 returns are threads like this

[http://ubuntuforums.org/archive/index.php/t-926101.html](http://ubuntuforums.org/archive/index.php/t-926101.html)
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/300121](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/300121)
[http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/](http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/)

---

