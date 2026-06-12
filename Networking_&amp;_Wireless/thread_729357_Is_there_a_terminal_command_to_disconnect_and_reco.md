---
title: "Is there a terminal command to disconnect and reconnect my usb wireless device?"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by Prism123 on 2008-03-19
Its recognized on wlan0, and using xubuntu if that matters.

Anyway situation is this old laptop I use occasionally, most for typing essays and occasional internet browsing while comfortably lying in bed, there is only one usb key.  This if I need to use another usb device such as a thumb drive I need to unplug the usb wireless adapter and then replug it back in later when I'm done with the other usb device.  Well problem is when i replug it in it does not reconect with my network, not even really sure if it realizes it has been reinserted.  So I usually open up the network gui, and disable it then reenable it and it then works fine.

So whats the problem with this?  Well the laptop is old, and for some reason most of the system tools, including network seem to run particularly slowly, and take a while to boot up.  Thus if I could open up a terminal, which starts much quicker, and just type something in it would be much easier and faster.  Is there a command that would do what i want, or even better is there a way to get xubuntu to automatically detect that I reinsterted my device and reconnect to my network.   I'm using a linksys wusb 11 v2.6 if that matters.

---

### Post by Junglizer on 2008-03-19
You should just be able to do this with the ```
iwconfig
``` and ```
ifconfig
``` commands. Either as root or using sudo.

---

### Post by (((X))) on 2008-03-19
Junglizer is right, use iwconfig to see what name your wifi interface has.
And then do
ifup wlan0(to bring that interface up)
and
ifdown wlan0
you will need sudo here as well

---

### Post by Prism123 on 2008-03-19
well, iwconfig recognizes my wireless adapter and calles it wlan0, but ifconfig doesn't have it listed so I can't use ifdown or up.  What commands would I use with iwconfig to accomplish the same thing?  Or is there a way to get ifconfig to recognize the device too

---

### Post by Prism123 on 2008-03-19
interestingly enough ifconfig does recognize the device after I disable and then renable it using the network gui tool thingy.  Is there a way to refresh it so that it without doing that after I've disconnected then reconnected the usb cord?

---

