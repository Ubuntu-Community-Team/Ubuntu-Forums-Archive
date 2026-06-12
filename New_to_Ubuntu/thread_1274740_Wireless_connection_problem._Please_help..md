---
title: "Wireless connection problem. Please help."
date: 2009-09-24
forum: New to Ubuntu
---

### Post by Halfbrainhunter9000 on 2009-09-24
I am completely new to ubuntu as well as Linux and I'm having a hard time connecting to my wireless Internet. I have a broadcom BCM4306 wireless card. I have tried the broadcom drivers and I tried to figure out NDISWRAPPER but no luck. Any and all help would be much appreciated.

---

### Post by skatinjj on 2009-09-24
**Assuming you have ndiswrapper installed run from the terminal:**
```
ndiswrapper -i nameofdriver.inf
```

**then**
```
ndiswrapper -l
```

to verify it installed.

As you can see, you use the .inf file to install the windows driver.

---

### Post by Halfbrainhunter9000 on 2009-09-24
Okay, I tried that and it said that there was no such file or directory at "/usr/sbin/ndiswrapper-1.9"
:confused:

---

### Post by Bucky Ball on 2009-09-24
DO NOT use ndiswrapper. That has been superseded for most Broadcom cards. If you haven't done it already plug in an ethernet cable and get updates. You card should be picked up and you will be offered the appropriate restricted drivers.

The driver you should be using is B43. System->Administration->Hardware Drivers and make sure it is not there already and disabled.

Repeat, AVOID ndiswrapper at all costs. It is no longer used for these cards and you can usually only get it to work with Broadcom cards if you are lucky enough to have a fairy sitting on your head.

---

### Post by jomarlinga on 2009-09-24
wahuhu..di po ako tutulong ,,,kudi papatulong din on how ko ma lolock ung WIFI connection d2 sa haus lng ng di lumalabas sa kapitbhay kc nakakasagap po cla,,slamat

---

### Post by skatinjj on 2009-09-24
Go into snaptic or adept (whichever is on your system) and search for ndiswrapper.

From the list that appears choose ndiswrapper-utils and ndisgtk, mark for install and apply changes.

run ndisgtk, navigate to where your drivers are and choose the .inf file.


nvm if it isnt used for Broadcom cards, sorry.

---

### Post by Bucky Ball on 2009-09-24
> **skatinjj said:**
> Go into snaptic or adept (whichever is on your system) and search for ndiswrapper.

From the list that appears choose ndiswrapper-utils and ndisgtk, mark for install and apply changes.

run ndisgtk, navigate to where your drivers are and choose the .inf file.


nvm if it isnt used for Broadcom cards, sorry.

WRONG! As mentioned, ndiswrapper is superseded for these cards and B43 was developed. These cards should now work 'out of the box' and if they don't it will take only a little tweaking. Ndiswrapper is the nightmare route and you may never have any success using it.

Plug in a cable.

---

### Post by anewguy on 2009-09-25
Well, ndiswrapper still works with these cards, and some people have actually reported problems using the B43 drivers.  I think it is more a matter of taste and trying things to see which works best for you.  A key point being overlooked here is that if the user does use ndiswrapper, B43 and a couple of others (I'd have to look again to see which) need to be added to blacklist or NEITHER driver will work because they conflict with each other.  Also, if using ndiswrapper, there is a little more to it than what was mentioned - ndisgtk can help there to avoid additional manual steps (I don't know it ndisgtk takes care of any blacklisting or not).

dave :)

---

