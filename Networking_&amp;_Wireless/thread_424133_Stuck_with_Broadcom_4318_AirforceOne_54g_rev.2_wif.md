---
title: "Stuck with Broadcom 4318 AirforceOne 54g rev.2 wifi card on Fujitsu-Siemens notebook"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by belekas on 2007-04-26
Hello brothers and sisters(if any):)

I just swithed to Ubuntu 7.07 Feisty and the Bcm43xx doesnt work. I tried all the methods and still nothing works. My card gets detected as eth1 with ndiswrapper but still nothing happens and i cant turn the light on because the WIFI button doesnt work like it works nicely on winxp. i need this WIFI card going badly but im out of ideas anyone could help me i would be very glad and would leave without some present or something;) we can talk on skype if anyone can take care, because im sick and tired booting from ubuntu to winxp to read and then restarting to ubuntu to try and get nothing:(

Any help is appriciated!

Thank you in advace

Peace!

---

### Post by sharpycore on 2007-12-22
Does your wireless card need a hardware switch to turn it on? If so, have a look at one of my past posts (there aren't many) for how to solve it.
Tom

---

### Post by stunner on 2007-12-22
Whoa - tearing open your system is a little extreme.  I have the same card and it gave me headaches at the start as well.

First, are you trying to use ndiswrapper or the open-source bcm43xx driver?  You can't use them both at the same time.  I would recommend using ndiswrapper.  You can start with this thread: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=197102](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=197102)

---

### Post by sharpycore on 2007-12-22
> **stunner said:**
> Whoa - tearing open your system is a little extreme.  I have the same card and it gave me headaches at the start as well.

First, are you trying to use ndiswrapper or the open-source bcm43xx driver?  You can't use them both at the same time.  I would recommend using ndiswrapper.  You can start with this thread: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=197102](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=197102)

There are certain hardware swtiches that can literally only be activated by taking the laptop apart. I wasn't suggesting they jump straight into it but some bcm4318 cards are plugged into a fujitsu mobo that needs the hardware switch overriding for it to work.
Tom

---

### Post by stunner on 2007-12-23
I should consider myself lucky then - my hardware switch works fine.  Good to know though.  Thanks for the info.

---

