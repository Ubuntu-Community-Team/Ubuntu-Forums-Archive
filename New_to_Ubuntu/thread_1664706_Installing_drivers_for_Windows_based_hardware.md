---
title: "Installing drivers for Windows based hardware"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by formzee on 2011-01-11
So I installed Ubuntu last night and am faced with my first issue, hopefully not the first of many!
Knowing almost nothing about LInux based systems, I was wondering if anyone could give ma a brief outline as to how I would go about installing the driver for Windows based hardware, namely the driver for my wireless keyboard?

---

### Post by jerrynewt on 2011-01-11
So far on all of my installed linux systems (back to 6.04 distribution) I just hooked the wireless keyboard and mouse up, booted the system and it worked out of the box.

---

### Post by Mark Phelps on 2011-01-11
> **formzee said:**
> So I installed Ubuntu last night and am faced with my first issue, hopefully not the first of many!
Knowing almost nothing about LInux based systems, I was wondering if anyone could give ma a brief outline as to how I would go about installing the driver for Windows based hardware, namely the driver for my wireless keyboard?

Drivers for peripherals (such as mice, keyboards) are installed as part of the initial setup -- which is why, with Linux distros, you do NOT insert a driver CD immediately after initial installation.

IF these are Windows drivers -- you can't use them. These drivers won't work with Linux distros.

---

### Post by bodhi.zazen on 2011-01-11
> **formzee said:**
> So I installed Ubuntu last night and am faced with my first issue, hopefully not the first of many!
Knowing almost nothing about LInux based systems, I was wondering if anyone could give ma a brief outline as to how I would go about installing the driver for Windows based hardware, namely the driver for my wireless keyboard?

In general, Linux is not windows and you can not use the windows drivers.

Probably easier to use an alternate keyboard, google search the keyboard or tell us what it is.

---

### Post by eriktheblu on 2011-01-11
For most hardware specific drivers are not required. If it does not function automatically (make sure it's turned on, charged, and employ the connect buttons first), your best bet for a solution is a Google search (Ubuntu <version> <keyboard model>)

---

### Post by formzee on 2011-01-13
this is the keyboard [http://www.ortek.com/prod_detail.asp?pid=131&id=156&ppid=101&cname=Keyboard%3E%3EWireless%20Keyboard%3E%3EWKB-2000S](http://www.ortek.com/prod_detail.asp?pid=131&id=156&ppid=101&cname=Keyboard%3E%3EWireless%20Keyboard%3E%3EWKB-2000S)

pretty obscure make so I doubt there's much chat about it. Sorry to sound like a total noob but  is this not what ndiswrapper is for i.e using windows based products?

---

### Post by bodhi.zazen on 2011-01-13
> **formzee said:**
> this is the keyboard [http://www.ortek.com/prod_detail.asp?pid=131&id=156&ppid=101&cname=Keyboard%3E%3EWireless%20Keyboard%3E%3EWKB-2000S](http://www.ortek.com/prod_detail.asp?pid=131&id=156&ppid=101&cname=Keyboard%3E%3EWireless%20Keyboard%3E%3EWKB-2000S)

pretty obscure make so I doubt there's much chat about it. Sorry to sound like a total noob but  is this not what ndiswrapper is for i.e using windows based products?

For windows wireless drivers yes but not any and all wireless cards work, and it is not for video drivers or other hardware.

You will need to use the power of google

[http://ubuntuforums.org/showthread.php?t=1594007](http://ubuntuforums.org/showthread.php?t=1594007)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405390](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405390)

[http://patchwork.ozlabs.org/patch/45738/](http://patchwork.ozlabs.org/patch/45738/)

---

