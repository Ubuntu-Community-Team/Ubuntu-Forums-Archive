---
title: "Wvidial dials too slow, so can't get signal"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by richterlevania3 on 2008-09-25
Hi there,

Something must had happened with my fresh install, without dual-booting XP: a series of problems appeared and, after setting my system the way I like, I'm not inclined to redo all the work again to see if everything goes fine again (my net is a trash). So, I'm trying to solve all the problems. Besides, this is good 'cause it forces me to learn more.

Now I have a problem with wvdial: before and after the fresh install it was working nice. Suddenly, last Monday, when I tried to connect to my GSM ISP, it started and began to try to connect - nothing wrong until then. So I noticed it was longing too much to connect: I looked the log while it was dialing and noticed it was doing it waaayyyyyy too slow. Before it would do like this:

Modem initialized
Sending ATZ
Sending Init some code here
Waiting carrier
NO CARRIER! Trying again...

Sending Init some code here...

Between "Waiting carrier" and "NO CARRIER! Trying again..." it longs like 10 secs now, when it used to long only 1 sec or less. Too slow, so it can't get the signal ever. When it was normal, it used to repeat the dial like 10 times in 7 secs before the connection was succesful. Now, the same 10 tries longs 2 minutes or more, never catching the carrier signal.

WTF?!?

Someone has an idea of what's happening? I tried to uninstall completelly wvdial and gnome-ppp to see if it would make a difference: nothing here. I tried to use wvdial alone too: it made it like gnome-ppp did.

---

### Post by timcredible on 2008-09-25
could it be on a different port?  did you plug something else in that might have taken /dev/ttyUSB0, or whatever port your modem is using?

---

