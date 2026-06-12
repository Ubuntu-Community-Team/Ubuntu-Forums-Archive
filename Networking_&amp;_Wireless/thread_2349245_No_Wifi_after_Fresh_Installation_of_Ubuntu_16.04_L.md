---
title: "No Wifi after Fresh Installation of Ubuntu 16.04 LTS"
date: 2017-01-12
forum: Networking &amp; Wireless
---

### Post by balamurthy83 on 2017-01-12
Hello Friends !

I tried installing Ubuntu 16.04 LTS on my Windows HP Pavilion X360. As posted by several users I could not get Wifi option at all. Tried following several solutions posted in this forum, but no luck.
Initially, i atleast had the wifi network toggle option in network settings but after attempting several solutions posted in forums, that disappeared  even. 

I have attached the output of network script here. Any help towards this will be great. Thanks in advance.

---

### Post by Hadaka on 2017-01-12
Hi, please open a terminal and do..
```
modinfo iwlwifi | grep 3165
```
*If you get nothing...no output, then from a working wired
connection please copy and paste..
```
sudo apt-get install linux-generic-hwe-16.04-edge
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux-firmware_1.161_all.deb
```
remove the wired connection,any usb devices,BOOT and test wireless.
thanks.

---

### Post by balamurthy83 on 2017-01-12
That worked like a charm ! Thanks a million Hadaka.

Can you also please explain what each of the above command does. On a high level, I understand that the last 2 command downloads and installs the WLAN  driver for this OS. I don't understand the first command.

---

### Post by Hadaka on 2017-01-12
Hi..glad that worked for you.

sudo apt-get install linux-generic-hwe-16.04-edge *<<-- This line installs the 4.8 kernel..required for your Intel wifi card*

wget [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb) <--This gets the firmware required

sudo dpkg -i linux-firmware_1.161_all.deb <-- This installs the firmware to your computer.

Please mark your thread SOLVED by clicking THREAD TOOLS near the right top area of your thread
and then choose SOLVED
thanks.

---

### Post by Gurpinder Kaur Chahal on 2017-04-28
Hi, 
Thanks a lot! This worked for me too. I tried so much of the stuff from the Internet, but this one is perfect.
Thanks again

---

