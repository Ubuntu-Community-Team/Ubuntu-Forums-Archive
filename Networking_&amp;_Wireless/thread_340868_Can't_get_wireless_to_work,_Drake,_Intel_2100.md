---
title: "Can't get wireless to work, Drake, Intel 2100"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by acranox on 2007-01-17
I just got a Dell D600, it has the Intel 2100 wireless card.  I've just installed Ubuntu 6.06 on it.  I can't get the wireless card to connect to my router.  Ubuntu seems to be seeing the card, but it looks like the radio is off, and anything I do to try and turn it on does nothing.  I've been reading the forum, and googling for at least an hour, but I can't figure this one out.  Can someone help me out?

--Peter

---

### Post by acranox on 2007-01-18
So anyhow, last night I eventually got it working, but only partly.  According to iwconfig, the Power was still off, and according to the applet in the panel, it also wasn't live, and I had to turn all security off, but I did get a connection.  Does that make any sense?  How do I get it to work with WPA security?

---

### Post by ingo on 2007-01-26
I ran into probs, too, and tried configuring wpa_supplicant by hand at first. Then stumbled across knetworkmanager. This is a nice programme which does all the wpa stuff for you! For it to be able to do that you have to get rid off all my wpa_supplicant conf files which you tinkered with manually. So I ran

sudo apt-get --purge remove wpasupplicant

I then installed knetworkmanager and reinstalled wpasupplicant via adept. Finally I had to check my 

/etc/network/interfaces

to see whether this was clean (no leftover wpa entries I had put in there) and seeing that it was ok I started knetworkmanager.

A dream!

---

