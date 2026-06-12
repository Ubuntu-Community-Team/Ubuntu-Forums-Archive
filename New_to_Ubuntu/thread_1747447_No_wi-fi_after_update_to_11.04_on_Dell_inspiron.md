---
title: "No wi-fi after update to 11.04 on Dell inspiron"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Skankyfish on 2011-05-02
We're running Ubuntu 11.04 on a Dell Inspiron 1501.  The wireless connection was flawless on 10.10, but after updating to 11.04 it just won't work (though it was updated via wi-fi!).  It has a Broadcom BCM4311 wireless card.  

We've tried installing a new driver, in particular following this thread: [http://ubuntuforums.org/showthread.php?t=1737996](http://ubuntuforums.org/showthread.php?t=1737996)

We seem to have an identical problem, down to a file in /etc/modprobe.d/ containing: 

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

We've followed the steps in post #12 in that thread, but when we try to run ```
sudo rmmod wl brcm80211
``` we get an error saying terminal can't find module wl.  And because we're total, utter noobs, we're totally out of ideas.  Can anyone suggest what we can do, using idiot speak?

---

### Post by TeoBigusGeekus on 2011-05-02
Try with the windows drivers and [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by coffeecat on 2011-05-02
> **Skankyfish said:**
> We're running Ubuntu 11.04 on a Dell Inspiron 1501.  The wireless connection was flawless on 10.10, but after updating to 11.04 it just won't work (though it was updated via wi-fi!).  It has a Broadcom BCM4311 wireless card.  

We've tried installing a new driver, in particular following this thread: [http://ubuntuforums.org/showthread.php?t=1737996](http://ubuntuforums.org/showthread.php?t=1737996)

We seem to have an identical problem, down to a file in /etc/modprobe.d/ containing: 

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

We've followed the steps in post #12 in that thread, but when we try to run ```
sudo rmmod wl brcm80211
``` we get an error saying terminal can't find module wl.  And because we're total, utter noobs, we're totally out of ideas.  Can anyone suggest what we can do, using idiot speak?

Ignore the error. You're trying (I guess) to remove all traces of the proprietary drivers and use the new brcm80211 driver. Did you run **all** three lines:

```

sudo rmmod wl brcm80211
sudo modprobe brcm80211
sudo depmod -a
```... as suggested earlier in that thread? You need to modprobe brcm80211 after removing it with rmmod.

Also having "blacklist brcm80211" in /etc/modprobe.s/blacklist.conf doesn't seem to be very helpful when you're trying to use that driver. If the above three commands work, you might want to remove that line from blacklist.conf.

By the way, since I contributed to that other thread (not very constructively), I've helped someone install Natty to a netbook with a (different) Broadcom card. The brcm80211 driver works just fine with it. But that was with a fresh install. My guess is that your problems stem from residues of the STA and/or b43 drivers from Maverick and some of those blacklist.conf lines. You need to purge your system of the STA and b43 drivers and see if your card works with the brcm80211 driver.

---

### Post by yuni on 2011-05-22
This ons works fine for my inspiron 1501.

> **yuni said:**
> I have same problem with my inspiron 1501.

I solved my problem by using the following instruction.
 1. Remove additional driver
 2. Using Synaptic install firmware-b43-installer
The original info comes form here.
[http://askubuntu.com/questions/36905/no-wireless-with-dell-inspiron-1501](http://askubuntu.com/questions/36905/no-wireless-with-dell-inspiron-1501)

---

