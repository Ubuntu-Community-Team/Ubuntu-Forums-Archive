---
title: "Why does this happen?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by cyberjar09 on 2010-03-20
I have this problem with my Ubuntu bootup. Every once in a while, i get the screen i have attached with this thread during my bootup. What i fail to understand is as to why the screen does this? usually it ends at a small number and logs into Ubuntu correctly but this time it kept going until i typed my username and password in and now im here. 

btw, im an absolute noob whos has been in the microsoft camp all his life but now has discovered the power of open source. Im thoroughly loving it! =D

Thanks and much appreciated. 
Cyberjar09

---

### Post by blakep2 on 2010-03-20
it does that for mine as well sometimes. It dosent fill the whole page though.

---

### Post by sebastianabate on 2010-03-20
Do you have any usb hardware connected to your pc during boot? if yes, removing the usb hardware before boot makes any difference?

---

### Post by cyberjar09 on 2010-03-20
> **sebastianabate said:**
> Do you have any usb hardware connected to your pc during boot? if yes, removing the usb hardware before boot makes any difference?

yes I have lots of usb hardware connected. I have external drives, i have my webcam, my phone usb cable, my modem ... 

when i remove my external drive it loads wothout any problem. but why is it happening in the first place? I would like to boot my system up without having to disconnect and reconnect my usb drives over and over again. 

Thanks.

---

### Post by sandyd on 2010-03-20
> **cyberjar09 said:**
> yes I have lots of usb hardware connected. I have external drives, i have my webcam, my phone usb cable, my modem ... 

when i remove my external drive it loads wothout any problem. but why is it happening in the first place? I would like to boot my system up without having to disconnect and reconnect my usb drives over and over again. 

Thanks.
this means the USB driver is not initialized properly on a cold boot.

There was a similar issue in dapper I believe.

Whats the specs of the drive?

type? manufacturer? filesystem?

---

### Post by cyberjar09 on 2010-03-20
> **carlee said:**
> this means the USB driver is not initialized properly on a cold boot.

There was a similar issue in dapper I believe.

Whats the specs of the drive?

type? manufacturer? filesystem?

Its a western Digital 320GB external drive.

---

### Post by sandyd on 2010-03-20
thanks.
bug filed.

seems like its attemting to access the drive before the correct (propper) modules are loaded...

---

### Post by sandyd on 2010-03-20
and your using 9.10 right?
latest kernel?

---

### Post by cyberjar09 on 2010-03-20
> **carlee said:**
> thanks.
bug filed.

seems like its attemting to access the drive before the correct (propper) modules are loaded...

ok thanks alot.

---

### Post by cyberjar09 on 2010-03-20
> **carlee said:**
> and your using 9.10 right?
latest kernel?

2.6.31-20-generic when i type ```
uname -r
```

---

### Post by sandyd on 2010-03-20
good.
your using the latest kernel.


Check on:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543085](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543085) :)

---

### Post by sebastianabate on 2010-03-20
> **carlee said:**
> good.
your using the latest kernel.


Check on:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543085](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543085) :)


Or this one

[https://bugs.launchpad.net/linux/+bug/88530](https://bugs.launchpad.net/linux/+bug/88530)

---

### Post by FlyOutlaw on 2010-03-20
Mine does the same thing but it is because i have a different OS on the hard drive ahd have it set to boot from the external usb drive... tell the computer not to boot from the usb drive and it should work fine. Mine boots fine when I have no drive plugged in also the usb thumb drives work and it boots fine with them in 

Thanks
Later;)

---

### Post by cyberjar09 on 2010-03-21
> **FlyOutlaw said:**
> Mine does the same thing but it is because i have a different OS on the hard drive ahd have it set to boot from the external usb drive... tell the computer not to boot from the usb drive and it should work fine. Mine boots fine when I have no drive plugged in also the usb thumb drives work and it boots fine with them in 

Thanks
Later;)

I dont think my Asus M2N32SLI motherboard supports usb boot ...

---

