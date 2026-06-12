---
title: "Kyocera KPC650 EVDO Card Disconnects"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Danuary on 2007-05-15
Hi,

Long time Linux user, first time Ubuntu user. 

I have a Dell Latitude D620 running Feisty. In my PCMCIA slot is a Kyocera KPC650 EVDO card (Verizon Wireless). I've configured PPP for the card via the "Manual Configuration" section of the NetworkManager applet in GNOME; modem pointed to /dev/ttyUSB0, pretty much stock configuration other than that.

The card works great, except for one thing. I get disconnected after 2-5 minutes of being online. I thought at first it was spotty signal, but I've tried a bunch of different locations and have found I always get disconnected after a few minutes. I can immediately reconnect without doing anything crazy like unloading the module, but one can see how that might get to be a little frustrating ;-)

I'm not really sure where to look for info here; I've turned on debug in pppd and all it really tells me is that pppd times out and disconnects. No surprise there.

The card has worked properly in FC6 and Windows, so I'm trying to figure out what's different here in Feisty. What other debugging should I be enabling or looking at to try and figure out what's going on here?

Thanks!
d

---

### Post by absrao on 2007-05-29
Same story here.. 

kernel 2.6.20
Ubunty Feisty
Disconnects every 2.5 to 2.6 minutes.. 

Any pointers ?

---

### Post by Jim March on 2007-06-16
Do a search on KPC650.  There are a couple of solutions.  Mine is this bad boy:

[http://3gstore.com/index.php?main_page=product_info&cPath=35&products_id=99](http://3gstore.com/index.php?main_page=product_info&cPath=35&products_id=99)

Coolest thing ever.  I've posted about it elsewhere in more detail, a search will turn it all up.  Solves EVDO issues in Linux post-haste.

---

### Post by Mach1US on 2007-06-18
You have to edit PPP config file which is located in etc folder and add the following :
```
lcp-echo-failure 0
lcp-echo-interval 0
```
What is happening your connection process has timer set so certain value after which if it does not hear from the other side considers circuit broken where in fact carrier side is not set up for this type of circuit maintenance so all you need to do is edit this script .
Hope this helps.

---

