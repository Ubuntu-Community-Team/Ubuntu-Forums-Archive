---
title: "Ndiswrapper-wusb11 success"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by svenkatesan on 2008-01-26
I am using ubuntu-7.10 version.
In my previous installation with this adopter went without success but this time I have succeeded this way.
Those who still not out of woods may give a try.
Despite wusb11-v2,8 external wireless adopter recognizes it can't make any connection.
Here is the chronological action
From synaptic, search for ndiswrapper
It will show two files...install that.(I didn't install ndisgdk)
Next search for "build essential and header" files--- install these too.
To install all these you do not require internet connection.
Get ndiswrapper 1.50 version from other sources and install the with these driver.

  [COLOR="Red"]**_[http://www.esnips.com/web/ndiswrapdrivers](http://www.esnips.com/web/ndiswrapdrivers)_**[/COLOR]

In this folder I have given 2 files one for wusb11 and the other for zd1211.Since I have two adopters  I installed both.

Installation went with out any error.

Now configure your network either in graphical mode or terminal mode.

If this works give a big smile. :-)) and enjoy wireless.

Note: First I tried with my new installation of Fedora 8.It was ok until I update my system with 1GB.When I restart it crashed F8.When this splashed me to try on ubuntu and got exited.

Use the attached drivers on your own risk.I extracted the drivers using i6comp.

---

### Post by bwtranch on 2008-01-27
This driver should work w/o having to use a wrapper. Actually, using a wrapper often hangs it up. I'm speaking to you on it right now.

---

### Post by svenkatesan on 2008-01-28
Hi bwtranch
Though it recognized in  at76...chipset  and network manager can show wireless connection,internet could not accessed.
In my system I faced this problem on both time installation.

---

