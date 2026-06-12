---
title: "Really Slow Dial up connection"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by mdkaek on 2005-11-18
I have just successfully accessed the internet for the first time using a dial up connection with Ubuntu 5.04, but it is painfully slow.  I am using a US Robotics 56K external DataFax modem and would like to know if there is a way to show the speed I am connecting at and then if there is a way to increase that speed.  

Thanks in advance.

---

### Post by az on 2005-11-18
There are lots of ways.  Probably the one that I would use first is to open up a terminal and run

sudo apt-get update.


You should fetch the latest package data from the internet.  Unless the file is only really small, you will see your download rate on the right.

If you missed it, you can install a package and you will see the rate as you download it.

You can also just type:
wget [http://ca.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.0.7-0ubuntu20_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.0.7-0ubuntu20_i386.deb)

And you will see the download rate.

---

