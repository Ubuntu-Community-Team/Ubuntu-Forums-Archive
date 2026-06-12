---
title: "How To: Connect to a 3G mobile phone for Internet"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by TekNullOG on 2008-09-11
I was hoping to make a clear and easy tutorial for people to connect their laptops to the internet via a 3G mobile phone. I was looking to gather everyone's expertise into one clear "How To". 

There's no hiding that mobile internet is becoming really fast and data plans are becoming a little more realistic in price. 

Most tutorials or "How To"s in the forum explain how to do it with Bluetooth but... Bluetooth is really slow (speeds of 721 kbit/s for 1.2 and 2 mbit/s for 2.0) compared to the capacities of a 3G phone (I reach up to 5.5 mbit/s with my unlocked Nokia E71).

**How do YOU connect to the internet using your phone and preferably a USB cable? Do you get 3G speeds? What phone(s) did you test it with?**

Hopefully with everyone's feedback, I'll have enough content to write something pretty easy for everyone.

So far, I've found this post (thanks to [ukripper]("http://ubuntuforums.org/member.php?u=229569") on these forums) but have yet to try it. (but plan to before the end of the week)
[http://mynewn95.blogspot.com/2008/06/using-3g-modem-with-linux-ubuntu-804.html](http://mynewn95.blogspot.com/2008/06/using-3g-modem-with-linux-ubuntu-804.html)

It's basically:
- Install gnome-ppp using the Synaptic installer (or aptitude).
- Start gnome-ppp from the Internet menu
- Enter username and password (if any)
- Enter *99# in "Phone number"
- Press "Setup"
- Press "Detect"
- Chose type "USB modem"
- Press "Close"
- Press "Connect"

Has anyone tried this and do you reach 3G speeds? Feedback?

---

### Post by TekNullOG on 2008-09-11
Maybe I am ahead of time...
I just found this:

[https://wiki.ubuntu.com/3GNetworkingIntrepid](https://wiki.ubuntu.com/3GNetworkingIntrepid)

It also seems to be "high priority" on Launchpad's site:
[https://blueprints.launchpad.net/ubuntu](https://blueprints.launchpad.net/ubuntu)

Does this mean that it doesn't work yet or does it mean that it isn't simple to do yet?

---

### Post by FBulovic on 2008-09-13
My mobile carrier doesn't have 3G but procedure is the same for GPRS, EDGE, 3 or 3.5 G. Avoid BT for 3+ G connection, just use microUSB-USB cable. I have described procedure on [www.2010-solutions.co.za](www.2010-solutions.co.za).

Cheers
F Bulovic

---

