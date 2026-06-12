---
title: "cpu info display"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by stans on 2009-11-08
What command will provide information about my cpu ? I've tried lshw, hwinfo, discover, but no Pentium model number is returned.  I've seen a reference to 'Device Manager' but cannot find it in my menus (Karmic).

I know that it is a Pentium 4 dual cpu running 3.0Ghz... but would like to know more details.

---

### Post by dox_drum on 2009-11-08
> **stans said:**
> What command will provide information about my cpu ? I've tried lshw, hwinfo, discover, but no Pentium model number is returned.  I've seen a reference to 'Device Manager' but cannot find it in my menus (Karmic).

I know that it is a Pentium 4 dual cpu running 3.0Ghz... but would like to know more details.

Try with 
```
sudo lshw > lshw.txt
less lshw.txt
```

There will be all the information or CPU, network, graphic card, etc.

---

### Post by Zoot7 on 2009-11-08
```
cat /proc/cpuinfo
```
Tells you pretty much everything.

Talking of system information; Hardinfo is a nice system information tool across the whole system.
[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)

Check it out. :)

---

### Post by Hetepeperfan on 2009-11-08
> **dox_drum said:**
> Try with 
```
sudo lshw > lshw.txt
less lshw.txt
```There will be all the information or CPU, network, graphic card, etc.


Another good option that works for me is:

lshw -short

which can ofcourse also be redirected to any file

---

### Post by stans on 2009-11-08
Thank you for the replies.

Although cpuinfo shows lots more than lshw, it doesn't show the model. 

I'm trying to use the power supply estimator and one of the questions pertains to the actual model... such as 53000.

---

### Post by Zoot7 on 2009-11-08
> **stans said:**
> Although cpuinfo shows lots more than lshw, it doesn't show the model. 
Hmm.. this is what I get:
> model name	: AMD Phenom(tm) II X4 955 Processor

Is that what you mean?

---

### Post by stans on 2009-11-08
The ASUS power supply wattage calculator offers a lot of different types of pentium 4 to select from. Maybe I am looking for more detail than I really need.

---

### Post by Zoot7 on 2009-11-08
If you're shopping for a new power supply, by all means post your hardware specs here, maybe we can be of help. :)

---

### Post by stans on 2009-11-08
Thanks for the offer to assist. Very much appreciated. I have a nearly new power supply - 650w - and doubt that my problem is power supply related. I've chased this down for months now, first on Jaunty and now on Karmic... it's the usb mouse freezing, but nothing else on the system freezing. 

At sort of a dead end now on this...

---

### Post by Zoot7 on 2009-11-08
Yeah i'd say you can safely disregard the power supply problems. ;)

I've done quite a bit of googling about the mouse problem, but it seems that it's a bug in Karmic; and the solution seems to be, revert back to either Intrepid or Hardy which isn't much use to you sadly.

Out of interest did it work okay before Jaunty?

---

### Post by stans on 2009-11-08
It's nice to know that I am not alone with this fiasco of the usb mouse.

It started in Jaunty when the usb mouse was installed, and it was very annoying. 

Slightly annoying now (I've booted twice now in half an hour), but I still cannot get serious about deploying any applications. 

I did open a bug report while running Jaunty - never did hear back from them.

---

