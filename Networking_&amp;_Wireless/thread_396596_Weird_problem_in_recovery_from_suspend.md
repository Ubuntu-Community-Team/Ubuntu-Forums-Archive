---
title: "Weird problem in recovery from suspend"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by teddmeister2 on 2007-03-29
Okay, so i guess this was probably as good a category as there is on this, and it involves getting back wireless internet signal after coming out of "suspend".  But this problem requires a little setup:
I installed ubuntu edgy on my inspiron notebook now dual-boot xp and edgy.
Having a broadcom 4318 wireless card in may laptop, my introduction to linux was a sort of trial by fire; so I eventually followed the RIGHT howto and, after installing the gnome NetworkManager .6.3 along with the more complicated hoops you have to jump through to use broadcom wireless, WPA security, etc, I finally could use wifi in ubuntu.  Eventually, Ubuntu has become the primary OS on every computer in our house, and I've become a full-fledged ubuntu fanatic.  But, I digress.
There's an odd problem with my wireless connection when recovering from suspend mode.  But this only happens when I go into suspend mode while in the range of *one* wireless network and come out of suspend outside the range of said network/inside the range of another network.  But it doesn't just *fail to recognize* any wireless networks; rather, NetworkManager ceases to even recognize wireless networking or enabling it as an option *at all*.  In order to get wifi to work again I must reboot. :-k really weird.  So, anyway, what I want to know is how to **solve** this problem.  There is an only slightly inconvenient workaround for this problem that I currently use involving a logout prior to suspend.  So, any suggestions?

---

### Post by teddmeister2 on 2007-03-30
anybody?
Is there anybody that has had this same problem but with a different setup, so that where the problem is can be narrowed down?  For example, Is there anyone with a non-broadcom card that has this happen?  Anyone without gnome networkmanager have this happen?  Anyone with a similar wifi setup *not* have this problem?

thanks.

---

### Post by mertle on 2007-04-04
Well, I currently have the same problem and upon searching upon a few forums, these two solutions/workarounds seem promising. Can't take credit for them, just stumbled upon them. I haven't tried either, yet, but I already have 'em saved for when I feel like troubleshooting.

SOLUTION 1: Disable, then re-enable your wifi driver

[INDENT]1. 'disable wireless' from within NetworkManager
2. $ sudo rmmod ipw2200
3. $ sudo modprobe ipw2200
4. 'enable wireless' within NetworkManager

( I have an Intel Pro Wireless 2200, aka 'ipw2200', use whichever name your wifi module goes by )[/INDENT]

SOLUTION 2: /etc/network/interfaces edit

[indent][http://knowledge76.com/index.php/Network_manager_applet]("http://knowledge76.com/index.php/Network_manager_applet")[/indent]

Hope these are at least helpful. :)

- mertle

---

### Post by huzzak on 2007-04-13
I'm running Ubuntu Edgy on a HP Pavilion laptop dv5237cl.  The same thing happens to me.  I thought it was random, but I'll check to see if it is just when I change network domains during suspend.  I haven't tried either of these fixes yet, but when it happens again, I will and I'll post how it went.

---

### Post by huzzak on 2007-04-13
I didn't mvoe from where I was sitting and the wireless works just about every other time when I come back from suspend.  When it isn't working the two commands suggested in the first solution from mertle work fine for getting the card back up and running.  The second solution does nothing for this particular problem.  Thanks mertle, now I shan't have to reboot so darn much.

---

