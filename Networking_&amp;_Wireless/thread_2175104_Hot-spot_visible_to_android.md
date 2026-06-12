---
title: "Hot-spot visible to android"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by stefano91 on 2013-09-17
I can create Wi-Fi hotspot with my ubuntu 12.04, and they work fine with other PC. 
Instead they are not visible to andorid devices. This is a known issue for andorid. On windows the problem has been avoided using connectify (as far as I read, I haven't tried out by myself). This kind of hot-spot is visible to andorid devices.
Is there a way to do the same with Ubuntu? 

Thank you very much!!!

---

### Post by Yogaraj on 2014-04-13
hi! you have to install ap-hotspot
open the terminal and type
#sudo su
#sudo add-apt-get repository ppa:nilarimogard/webupd8
#aptitude update
#apt-get install ap-hotspot
#ap-hotspot configure
#ap-hotspot start
now u can get connected with wifi visible to android devices

---

