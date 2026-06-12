---
title: "Boggling Modem Phenomenon"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by mertle on 2007-02-09
**EDIT:** AACK! I /do/ have wireless capabilities... crapola. Apparently, I was unknowingly tapping into a neighbor's connection. Hell, I didn't even KNOW I had wireless capabilities... I remember opting out of a wireless package when getting the system, so I never even bothered to check. Jeez. Can I get in trouble for that? Don't need someone comin' banging on my door yelling at me.

I disabled my wireless, though, and now my dialup modem stopped working (logging in through Windows, now). Then again, I dunno if it ever was working if I've been unknowingly logging into the 'ether' for the last two days. And here I thought I had some magical modem. Blargh. *snickers*

- mertle

-----------------------

Quite a novice Linux user, here.

This really isn't a *problem*, per se, but it's making me oh so curious. Ever since I've installed Kubuntu, I've been able to connect at very high speeds with just my Conexant HSF 56K modem (with third party drivers). I can't explain it, but I'm used to being able to DL a 3 MB file in about 10-15 minutes, but now it's under 45 seconds. There's no way I've found, so far, where I can actually see what rate I'm connecting at since KPPP isn't even running- it seems to connect on startup invisibly. How is this possible? And more so, how can I see how the hell I'm connected without even having to dial in manually w/ KPPP?

I know I'm not accidentally picking up on someone else's network somewhere in the ether 'cause I have no wireless capabilities. I'm connected simply by a household telephone line, no DSL.

Now, while I LOVE being able to have a (fake) high speed connection, I'm not sure that I like my computer just connecting to the 'net without me even knowing- it unsettles me. Nowhere in my system can I see that I'm even connected, yet here I am, surfing and DLing files at 100+ k/sec when I'm used to only 5 k/sec. (WTF?!?!)

I'm running Kubuntu 6.10 Edgy on a Dell Inspiron 9300.
Conexant HSF softmodem w/ Linuxant driver.

Can someone help or provide some insight?

- mertle

---

### Post by christhemonkey on 2007-02-09
That is very very wierd :-s

You can check if ppp is starting automagically by doing this:
```
ps aux | grep ppp 
```

---

