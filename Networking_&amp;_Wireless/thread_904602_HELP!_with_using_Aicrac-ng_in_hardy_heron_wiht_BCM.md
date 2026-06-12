---
title: "HELP! with using Aicrac-ng in hardy heron wiht BCM4311 card..."
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by ElevenWarrior on 2008-08-29
hi, this is my first post here at Ubuntu fourms!
anyways I've got a Compaq F572US laptop, and I need to know how to use Aircrack-ng
I was told that I need to install a certain driver to use it properly.
CAN ANYONE HELP???:confused:
please tell me if you need more info.
thanks

---

### Post by ElevenWarrior on 2008-09-07
Anyone??? Please!!!!!!!!!

---

### Post by lswb on 2008-09-07
Look here: [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

You don't need special drivers or driver patches unless you intend to use what the aircrack people call "packet injection" In a moderately busy network, enough data packets can be recorded to crack a WEP key without packet injection.

---

### Post by ElevenWarrior on 2008-09-09
I know. I want to be WPA cracking, which require Packet injection. anyone have the drivers for my card/patches?

---

### Post by sleeping cat on 2008-09-10
I have a similar setup to you,:(
 have you aircrack to run yet?

---

### Post by sleeping cat on 2008-09-10
can anyone tell me how to run aircrack it seems to be installed but not listed. thanks

---

### Post by lswb on 2008-09-10
The information is on the aircrack web site. 

[http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

---

### Post by EXCiD3 on 2008-09-10
have you tried using backtrack 3 instead? its much more suited for network hacking as it has many drivers preinstalled along with all the software you would need.

---

### Post by ElevenWarrior on 2008-09-11
yes I tried BT3 and it woln't boot, I still haven't Got Aircrack-ng to work,,,,

---

### Post by ElevenWarrior on 2009-01-06
hey I fixed the problem so if anyone wants to know how just post here.

---

### Post by EXCiD3 on 2009-01-06
I'd be intrested in hearing how you got it working.

---

### Post by ElevenWarrior on 2009-01-09
oaky here it is, 
how to get packet injection to work with the BCM4311 or BCM43xx cards,
 in hardy heron 8.04 
(mainly on the Compaq laptop F572US)
1. install kernel check, ([http://kcheck.sourceforge.net/download2.html?agree=I+accept+these+terms+and+conditions](http://kcheck.sourceforge.net/download2.html?agree=I+accept+these+terms+and+conditions).)
update your kernel to 2.6.26  make sure that your wireless card (and sound) is enabled on the driver list.

2.after thats done (yes it will take a while)
do this....
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
restart the PC and then make sure injetion is running by doing this...
(note, you may need to change the device at the end of the command line to what ever card you have.)

first,
sudo airmon-ng start wlan1

sudo aireplay-ng -9 mon0
hope this helps.

---

### Post by le_ridicule on 2009-12-22
sorry ElevenWarrior, 
i have installed Karmic Koala 9.10, do you think that i can do the same operation that you have illustrated? thanks
 
(sorry if my english is wrong)

---

