---
title: "Trouble with broadcom wireless card"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by zjagannatha on 2007-07-30
I am having trouble getting my broadcom wireless card to turn on. The wireless card is disabled and I am unable to have it turn on.

After running

```
lspci | grep Network
```

the output was:

```
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

after running:

```
sudo lshw -C network
```

the output was:

```
  *-network:1 DISABLED
        description: Wireless interface
        product: BCM4306 802.11b/g Wireless LAN Controller
        vendor: Broadcom Corporation
```

and some other stuff.

First, did you have the same problem?

Second, how do I get my network card enabled?

If you don't know then can you point me in the correct direction please.

---

### Post by noob12 on 2007-07-31
Several people have had success following the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by kevdog on 2007-07-31
Not to overlook the obvious, but is the laptop wireless device turned on?? (Is this a built-in card??)

---

### Post by noob12 on 2007-07-31
Also, can you post the **entire** output of 
```
lshw -C network
```
This will show us the associated driver if there is one.

---

### Post by jml on 2007-07-31
Hang in there, getting wireless in general, and Broadcom cards in particular is very challenging.  Here are two sites that offered help that I found useful.

[http://forums.debian.net/viewtopic.php?t=7949&highlight=broadcom+wireless](http://forums.debian.net/viewtopic.php?t=7949&highlight=broadcom+wireless)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

In general terms what has to be done is to blacklist the Broadcom driver that Ubuntu installs.  Then make sure ndiswrapper is installed and use it to install the windows driver which usually is found on a system disk, or a restore disk that came with your computer, or wireless card.  Good luck.

Joe

---

