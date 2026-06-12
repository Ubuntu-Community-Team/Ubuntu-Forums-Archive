---
title: "Huawei e3131 mount error"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by nelight2 on 2013-10-27
Hi. I have a huawei e3131 and a ubuntu based system. When i mount it there is an error, but network works. Can you check what error is it and Is it serious? [http://s16.postimg.org/6lwhmy945/Screenshot_from_2013_10_27_23_02_37.png](http://s16.postimg.org/6lwhmy945/Screenshot_from_2013_10_27_23_02_37.png) Thanks.

---

### Post by Newbunto on 2014-06-24
I would guess that it has something to do with what is mentioned here. [http://www.raspberrypi.org/forums/viewtopic.php?t=18996](http://www.raspberrypi.org/forums/viewtopic.php?t=18996)

---

### Post by Newbunto on 2014-06-28
To elaborate on this ... the Huawei E3131 exposes 3 devices, namely a serial/modem device for the actual communication, a mass storage device for the microSD card that you can insert in the stick and a CD-ROM device that has the software for Windows on it. (Presumably the latter is implemented as some non-volatile storage internal to the stick to which the telco writes an ISO image.) The software isn't useful to someone running Linux and hopefully the stick will work for our purposes as long as the serial/modem device is working.

---

