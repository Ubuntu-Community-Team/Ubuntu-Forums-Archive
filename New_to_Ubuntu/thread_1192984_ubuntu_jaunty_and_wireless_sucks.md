---
title: "ubuntu jaunty and wireless sucks"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-06-20
so im coming to realize the flaws with jaunty jackalope and my hp pavillion dv4-1275mx. most are easy to resolve but now i've concluded that the wireless sucks. i mean im downloading at a rather small fraction of what i was with intrepid. my issue is this i really like the advances with jaunty such as my 15 odd second boottime is there a way i can have my cake and eat it too?

---

### Post by TeoBigusGeekus on 2009-06-21
```
sudo apt-get install wicd
```

---

### Post by PatrickMoore on 2009-06-21
it isnt an issue with network manager i connect to the internet and to my wireless at 100%. its just ridiculously slow example i was downloading an iso of ubuntu studio... it took over 9 hours. when it used to take only 1

---

### Post by bhadotia on 2009-06-21
> **PatrickMoore said:**
> it isnt an issue with network manager i connect to the internet and to my wireless at 100%. its just ridiculously slow example i was downloading an iso of ubuntu studio... it took over 9 hours. when it used to take only 1

What wireless card?

---

### Post by PatrickMoore on 2009-06-21
broadcom 4322ag

---

### Post by bhadotia on 2009-06-21
> **PatrickMoore said:**
> broadcom 4322ag

Ndiswrapper or the official linux drivers? Try switching between them.

---

### Post by PatrickMoore on 2009-06-21
> **bhadotia said:**
> Ndiswrapper or the official linux drivers? Try switching between them.

in using the broadcom sta driver i read about the ipv6 bug and after upgrading to a newer kernel my video doesnt work. im going to try a fresh install and take it from there

---

### Post by bhadotia on 2009-06-21
> **PatrickMoore said:**
> in using the broadcom sta driver i read about the ipv6 bug and after upgrading to a newer kernel my video doesnt work. im going to try a fresh install and take it from there

This time use ndiswrapper.

---

### Post by 3rdalbum on 2009-06-21
> **PatrickMoore said:**
> ...upgrading to a newer kernel my video doesnt work.

BEFORE doing a fresh install: If you manually install a video driver (i.e.  from the ATI or Nvidia websites) rather than use the Hardware Drivers program, you will need to reinstall the driver every time you update the kernel. This is because the kernel's internals change and ATI and Nvidia's drivers aren't smart enough to change along with them.

The Ubuntu versions are smart enough, but the stock ATI and Nvidia versions aren't.

As for your other problem, try lowering the bit rate of your card.

```
sudo iwconfig wlan0 rate 5.5M
```

5.5 megabits per second seems to be the sweet spot for many of the problematic wireless cards, but you can try other values. This setting does not persist across reboots but you can put that command, less the 'sudo', into the /etc/rc.local file and it will run on every boot.

---

