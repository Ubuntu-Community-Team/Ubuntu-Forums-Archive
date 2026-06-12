---
title: "wireless network problem on Feisty Fawn"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by wak_maximus on 2007-07-21
i cannot connect to my wireless connection..
but i can connect using windows..
so i think its not the network provider problem..

i not pretty sure how to configure wireless network in feisty fawn..
because i'm in college and the service was provided from college administration..
when i connect to wireless, it suppose to redirecting me to login page..
that's what happen in windows..
but it not happen in feisty fawn..:(

---

### Post by Floppyjoe on 2007-07-21
Does your wireless work in Ubuntu anywhere else other than at your college?
If yes, then have you considered installing VMWare Server on your Ubuntu computer and loading Windows using VMware in Ubuntu. If your wireless does not work anywhere else using Ubuntu then  it is probably not configured properly.

---

### Post by pjb515 on 2007-07-21
I just had a similar problem, wireless worked in Windows, but not in Ubuntu, on a pc which is a dual boot. The problem was that I had to set the wireless speed on the router to the speed of my wireless card, which is 11 mb per second. It had been set to Automatic by default, so Windows was ok with that, but not linux. So maybe it's a similar thing on yours, configure the router manually to set the speed and everything to whatever you have set in linux. Good luck!

---

