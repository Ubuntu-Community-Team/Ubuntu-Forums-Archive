---
title: "RTL8187B, works on 8.10, but still has problems"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by T_N_T on 2008-11-29
The RTL8187B in my Gateway Notebook works, but I have to be almost right near my router to go anywhere on the internet.What I mean is that it almost has to be 100% signal strength to go anywhere when it gets down into the 80-70% range I am unable to surf anywhere. Is there any way to fix this or am I out of luck?

---

### Post by Fir3chi3f on 2008-11-30
A good place to start:
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

But just google rtl8187b and ubuntu i think this is easily fixable if that link doesn't help

---

### Post by lotacus on 2008-11-30
I have the same problem, the signal strength is horrid.

be careful following that guide because it's dated and for earlier kernel's. if your running 8.10 it works out of the box, but still the problem exists. btw 8.10 supports wpa2 ;)

---

### Post by Tom--d on 2008-11-30
Easy to solve.

Go to my thread here: [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

Explains and solves your problem :)

---

### Post by koala12 on 2008-12-01
I have the same NIC, and same problem. Please help.

I tried several distributions with new kernels but the problem always exists.

---

### Post by koala12 on 2008-12-01
setting the bitrate 5.5Mb work fine. I am posting on ubuntu far away from access point.

> iwconfig wlan0 rate modulation fixed
wiconfig wlan0 rate 5.5M

---

### Post by T_N_T on 2008-12-04
> **Tom--d said:**
> Easy to solve.

Go to my thread here: [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

Explains and solves your problem :)


Hey Tom,

I did what you said and now I can't even connect to the network, my network is 128-bit encrypted and it tries to "request a network address" and then it takes me back to the key enter box. Do you know what I am doing wrong?

---

### Post by T_N_T on 2008-12-04
Ok, I got it to work, though I had to turn off the WEP. Don't know why it won't work with 128 bit encryption.


Thanks for the help guys.

---

