---
title: "plz could any one help me in the configration of my usb modem"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by hish_3000 on 2007-08-28
i have a dial-up usb modem (aethra star modem um 1040) and my os is kubunu 7.04
i have download  ueagle-data-1.1.tar.gz
and after typing:

$ tar -xvzf ueagle-data-1.1.tar.gz 
$ sudo mkdir /lib/firmware/ueagle-atm
$ cd  ueagle-data-1.1/
$ sudo cp -a * /lib/firmware/ueagle-atm
 
the light of the modem started to flash and then stay on 
but my problem is : when itry to configure my modem by typing :

gksudo gedit /etc/ppp/peers/ueagle-atm

it say that it isnt installed 
im using this link to setup my modem :
[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)
plz help me

---

