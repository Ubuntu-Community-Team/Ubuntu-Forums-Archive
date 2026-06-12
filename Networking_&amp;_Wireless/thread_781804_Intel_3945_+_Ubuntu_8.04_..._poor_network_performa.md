---
title: "Intel 3945 + Ubuntu 8.04 ... poor network performance..."
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2008-05-04
This test is done using Ubuntu's 3945 drivers (free drivers)

One access point, one device, the laptop.  54Mbit connection.
transfer to a (fast,idle)file server.

File: 850MB XviD 

XP 32bit:
transfer time: 6 minutes 29 seconds 
CPU utilization: 16-19%


Ubuntu 32bit
transfer time: 8 minutes 32 seconds
CPU utilization 16%


This is >2 minutes slower than XP, or +25% longer time.
Data-rate during the copying is 1,6-1,7 MB/s 

Why is it like that ? - and what can I do to fix this ?

---

### Post by syko21 on 2008-05-04
Try using ndiswrapper with the intel windows driver. Instructions are here [http://ubuntuforums.org/showpost.php?p=4790682&postcount=10](http://ubuntuforums.org/showpost.php?p=4790682&postcount=10)

---

### Post by klange on 2008-05-04
In general, I've found the new free drivers to be quite poor. I continually lose my network connection, most of the time without actually losing the connection (I still *appear* to be connected to a network, but all attempts to do anything fail).

---

### Post by Kevbert on 2008-05-15
Try this link: [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

---

