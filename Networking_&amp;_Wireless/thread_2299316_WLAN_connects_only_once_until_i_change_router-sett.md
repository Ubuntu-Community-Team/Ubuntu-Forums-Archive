---
title: "WLAN connects only once until i change router-settings"
date: 2015-10-17
forum: Networking &amp; Wireless
---

### Post by Zockermike on 2015-10-17
Hi guys,

ive encountered a pretty strange problem:

First of all: i'm pretty new to Linux and google didn't help me, so i thought i directly ask the pros. I use a ubuntu 14.04 with LXDE. And excuse my bad english since this is not my main language.

So i got the WLAN and the LAN on my work where everything connects fine. I got the WLAN of my university where everything connects fine.
And i got my WLAN at home, where everything connects fine... once!

to explain:
Day 1: Connecting doesn't work so i change my password from a superlong secure one to a long one.
-> Connection works directly after change.

Day2: Connection doesn't work again. So i delete the profile and add it again, still not working. Then i change 1 letter of the password, save & apply and immediately change it back to the old (long one).
-> Connection works fine

Day3: Connection doesn't work again (who would've thought THIS? -.-). I change the "Key renewal interval" from 3600 to 3601. I save & apply.
-> Connection works fine

Day4: Connection doesn't work again (yep, I'm not kidding you). So I change the "Key renewal interval" back to 3600. I save & apply the changes.
-> Connection works fine

Now thats my problem. Each day I'm trying to connect I first have to change some random thing in my WLAN settings on the Router to make it work.
I'm using a netgear with dd-wrt.

Does someone know this problem or has hints for me, where to start searching for the cause?

If you need logs or sth you need to tell me the commands to obtain them, i'm new to Linux.

Thanks for your help & kind regards,
Zockermike

---

### Post by Zockermike on 2015-10-22
112 views, no answer yet...

am i allowed to bump?

Greetings

---

