---
title: "No Wireless Ubuntu 13.10"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by viktor-hubinette on 2013-11-06
hi i cant see any wireless on my network meny and the only thing i can get internet from is ethernet so please help how do i fix so i can use wireless again

(updated from 13.04 to 13.10) and then the wireless got removed :( 

tell me what commands you need the output of :) Thanks

it can maybe be becouse i dont have a wireless driver or something becouse i haved problem with that on ubuntu 12.04 too


outputs: 

lsmod | grep rt1

- nothing


sudo modprobe rt18192cu

- FATAL: Module rt18192cu not found.

iwconfig

- eth0      no wireless extensions.

lo        no wireless extensions.


sudo iwlist wlan0 scan

- wlan0     Interface doesn't support scanning.


rfkill list all

- nothing

---

### Post by viktor-hubinette on 2013-11-06
bump

---

### Post by viktor-hubinette on 2013-11-07
bump

---

### Post by viktor-hubinette on 2013-11-09
hallo anyone?

---

### Post by van hanegen on 2013-11-09
Try this: [http://ubuntuforums.org/showthread.php?t=2148130&page=2](http://ubuntuforums.org/showthread.php?t=2148130&page=2)
(there is already a new version of rt18192cu driver  on realtek site, though)

Sorry, this is for rt**l**8192cu, not for rt**1**8192cu

---

### Post by NM5TF on 2013-11-09
> **van hanegen said:**
> Try this: [http://ubuntuforums.org/showthread.php?t=2148130&page=2](http://ubuntuforums.org/showthread.php?t=2148130&page=2)
(there is already a new version of rt18192cu driver  on realtek site, though)

Sorry, this is for rt**l**8192cu, not for rt**1**8192cu

Viktor you should definitely do this...it fixed my wireless problem
under Ubuntu 14.04 using the 3.11 & 3.12 kernels....

Tommy

---

