---
title: "wifi is connected but internet is not working"
date: 2015-12-08
forum: Networking &amp; Wireless
---

### Post by prasuna on 2015-12-08
Hi i am using dell inspiron laptop with operating system ubuntu 12.10 and windows. But in ubuntu wifi is connected but  internet is not working. I have checked with my phone and friend's PC  that internet is working.
[INDENT]Please help me to resolve this problem.
[/INDENT]

---

### Post by wildmanne39 on 2015-12-08
Hi, welcome to the forum! 12.10 is outdated and there will not be any new updates for it so I recommend you upgrade to at least 14.04 then if you have trouble click on the wireless script in my signature and post the information from the file it creates and someone will help you.
Thanks

---

### Post by prasuna on 2015-12-19
Hi, As internet is not working i am unable to fetch data from the below link..

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \

and unable to run the update commands:

sudo apt-get update
sudo apt-get dist-upgrade


Can you please help me run the wireless info script in any other way.

---

### Post by pqwoerituytrueiwoq on 2015-12-19
use a flash drive to get the script to the computer

post the output of this command
[FONT=courier new]lspci|egrep -i "ethernet|wireless"[/FONT]
then we can see what wireless card you have, if it is a usb wifi card run this:
[FONT=courier new]lsusb|egrep -i "ethernet|wireless"[/FONT]

---

