---
title: "Wireless broke on e1505 after enabling dual core"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by TuckWat on 2006-08-30
I just got my new Dell e1505 today and I installed ubuntu right away.  Everything is going pretty smooth, I installed 915resolution to enable my widescreen resolution and used this command to enable dual core:

sudo apt-get install linux-image-686

also did this:

sudo apt-get remove linux-image-386

When I select the 686 version through grub, my wireless card does not show up in Administration > Networking

Any idea why it isn't working now?

Thanks

---

### Post by Pdj79 on 2006-08-31
Just for your info, in order to enable dual-core support, you need to do the following:

sudo apt-get install linux-image-686-smp

As for the 686 kernel breaking wireless in an e1505, that's exactly what I'm using and my wireless is still intact...granted I had to switch my AP from WPA to WEP for the time being until I can get NetworkManager to support WPA.

---

### Post by TuckWat on 2006-09-18
tuckerw@tuckerw-laptop:~$ sudo apt-get install linux-image-686-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-686-smp


I'm pretty sure I have all the repositories enamled - what am I doing wrong?

---

### Post by Melcar on 2006-09-18
Have you tried reinstalling your wireless device (drivers)?  What method did you use to get your wireless working (did you have to install drivers for it or was it working from the start)? Expect issues with drivers when switching kernels.

---

### Post by ysr on 2006-09-18
> **TuckWat said:**
> tuckerw@tuckerw-laptop:~$ sudo apt-get install linux-image-686-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-686-smp


I'm pretty sure I have all the repositories enamled - what am I doing wrong?

Use this (without image in the name of the package)

```
sudo apt-get install linux-686-smp
``` 

See the link to package here

[http://packages.ubuntu.com/dapper/base/linux-686-smp]("http://packages.ubuntu.com/dapper/base/linux-686-smp")

Incidentally, I did not have any problems with the network card either.

---

### Post by cjazinski on 2006-10-22
I had the same problem but doing the linux-686-smp worked instead of the image one. hope that helps

---

