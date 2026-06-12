---
title: "Mount Android (HTC desire) over Bluetooth"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by djmac on 2010-08-13
Hi there,

I am interested to know if anyone has had any luck mounting their Android phone via bluetooth. I used to have a nokia and had no troubles with that; was quite simple. Haven't had any luck so far with the Android, Have tried obexfs (but perhaps incorrectly?)



Relevant Info (maybe):

Android version 2.2
Ubuntu version 10.04
Phone type HTC desire  (rooted)

Thanks for your help!

---

### Post by djmac on 2010-08-13
I have had some success (with obexfs):

```
sudo mount -t fuse "obexfs#-bXX:XX:XX:XX:XX:XX" /mnt/phone
```

Seemed to do the trick,(replace XX:XX:XX:XX:XX with your MAC address). Also, it is important to make sure the FTP server is switched on within the Android. 


NB: To find your phone's MAC address, use:
```
 hcitool scan
``` 
(make sure the phone is discoverable too)

---

### Post by hyperplus on 2012-01-07
Can anyone expand on how to set the FTP Server on?

---

### Post by cheatos on 2012-01-07
Maybe also, wether this is possible to do with the iPhone?

---

### Post by hyperplus on 2012-01-07
I posted the solution and explanation over this forum:
[http://forum.xda-developers.com/showthread.php?p=21129793#post21129793](http://forum.xda-developers.com/showthread.php?p=21129793#post21129793)

---

