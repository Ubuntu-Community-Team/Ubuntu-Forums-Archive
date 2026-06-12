---
title: "Wifi switch on"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by Sandy0848 on 2011-04-18
For some unknown reason I had a catastrophic failure of Ubuntu and was obliged to reload 10.10.

Before the failure the wifi on my Compaq laptop started up without fail but since doing the reload the wifi doesn't switch on.

When I do the alternative boot into Windows XP the wifi comes on at once.

Help !!!!

Sandy

---

### Post by Miljet on 2011-04-18
You might try opening System ->Preferences ->Network Connections, click on the Wireless tab, select your network, click Edit, and make sure that the Connect Automatically selection is selected.

---

### Post by Sandy0848 on 2011-04-29
Afraid I'm still without wifi on my laptop when using Ubuntu.

The laptop is a compaq which has a button to switch wifi on and of. When I load into XP the wifi switches on automatically. I am going to send this message using wifi very shortly.

However when I load into Ubuntu the wifi does not switch on automatically and despite my efforts I have not been able to find out how to get it switched on.

So we know that the wifi transmitter is working well and we know that this computer has worked previously in Ubuntu on wifi. Then I had a crash and haven't been able to get it up and working again.

Please take things slowly and steadily with me. I really do need your help.


Best wishes   Sandy

---

### Post by 3rdalbum on 2011-04-29
What is the chipset of the device? A quick look at the output of the following commands should help:

```
lspci
lsusb
```

(that's a lowercase L as in 'list', not an uppercase i, at the beginning of each of those commands).

And secondly, have you checked in Additional Drivers? You might need to download some non-Free firmware from there to get the wifi device to work. Obviously you'll need some sort of internet connection already running first.

---

### Post by Sandy0848 on 2011-04-29
> **3rdalbum said:**
> What is the chipset of the device? A quick look at the output of the following commands should help:

```
lspci
lsusb
```(that's a lowercase L as in 'list', not an uppercase i, at the beginning of each of those commands).

And secondly, have you checked in Additional Drivers? You might need to download some non-Free firmware from there to get the wifi device to work. Obviously you'll need some sort of internet connection already running first.


lspci    Broadcom BCM 311   802.11b/g
lsusb   Linux 1.1 root hub

and let me clarify I am using Ubuntu 10.04 and this whole assembly has worked well previously

Sandy

---

### Post by 3rdalbum on 2011-04-29
For Broadcom, you usually have to use Additional Drivers to get the right stuff to run the wifi device. Get an internet connection on your computer by plugging in an Ethernet cable into your computer and the router, reload your package list, and then go to Additional Drivers and you should be offered a driver.

Also, I note that in your earlier post you said you used to run 10.10, and in this latest post you say you're now running 10.04.

10.10 has more drivers than 10.04; if 10.04 doesn't have the right driver for your device then you should use a more recent Ubuntu like 10.10 or 11.04. Preferably 11.04 so we'll all be on the same page in terms of support.

---

### Post by Sandy0848 on 2011-04-30
> **3rdalbum said:**
> For Broadcom, you usually have to use Additional Drivers to get the right stuff to run the wifi device. Get an internet connection on your computer by plugging in an Ethernet cable into your computer and the router, reload your package list, and then go to Additional Drivers and you should be offered a driver.

Also, I note that in your earlier post you said you used to run 10.10, and in this latest post you say you're now running 10.04.

10.10 has more drivers than 10.04; if 10.04 doesn't have the right driver for your device then you should use a more recent Ubuntu like 10.10 or 11.04. Preferably 11.04 so we'll all be on the same page in terms of support.

Hope the sun is shining in west australia. It certainly is in belgium thanks to your help and encouragement.

Tried to go down the upgrade path this morning and started by installing all the updates shown for current version, 10.4.

Then tried to upgrade to 11.04    but couldn't find a way to do that.

Then in system-administration - hardware drivers was offered two different drivers for broadcom wifi. installed B43 driver ndrestarted and up came the little blue lilight and made it home from there.

Still cant imagine why it crashed in  the first place.

many thanks for your support

Sandy

---

