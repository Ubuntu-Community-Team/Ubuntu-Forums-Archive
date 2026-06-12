---
title: "USB Wireless Microsoft Network Adapter --&gt; Drivers installed setup assistance needed"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by sheeep on 2006-11-08
I managed to get the drivers required for my Microsoft USB adapter, model MN-510, to be recognized by the computer using the graphical version of ndiswrapper.

Right now I'm alittle stuck, the computer says that the mn510 drivers are installed and that the hardware is present.

I don't exactly understand how to configure the network.

My network is WEP encrypted, and I cant disable that right now...

When I enter sudo iwconfig I get returned:

> 

lo      no wireless extensions.

wlan0   no wireless extensions.

eth0    no wireless extensions.

sit0    no wireless extensions.



When I enter the Network Settings window, it says that the interface eth0 is active.

Any help or guidance is insanely appreciated, thanks.

---

### Post by sheeep on 2006-11-08
I hate to bump topics like this, but it has only gotten 2 views, and if I cant figure this out I'm gonna have to dish out the cash for xp.

---

### Post by tturrisi on 2006-11-08
You should not need ndiswrappper for the MN510 because it has a prism chipset, which is supported well in linux.

---

### Post by sheeep on 2006-11-08
Woah, that sets me back. It wasn't picking up the adapter, and I had read numerous times that you needed to install the drivers with either ndiswrapper or another method.

---

### Post by FrodoB on 2006-11-08
Take a look at:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

Specifically at:

[http://linux-wless.passys.nl/query_part.php?brandname=Microsoft](http://linux-wless.passys.nl/query_part.php?brandname=Microsoft)

I would have though that this driver was built with the kernel in Edgy, but evidently not?

As for Windows, there are a lot of sub $20 usb wireless devices that work with Linux, so why bother?

---

### Post by sheeep on 2006-11-08
I'm starting to think that part of the problem is I don't know how or what to do to configure the network, even if it is working.

---

