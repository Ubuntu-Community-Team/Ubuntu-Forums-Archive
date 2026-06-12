---
title: "Odd behaviour when watching videos or playing games online"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by JustSomeCanuck on 2014-05-18
Hello everyone,

I have a Toshiba Satellite L840D notebook computer with Realtek RTL8188CE wireless. Ubuntu 14.04 is installed, recently upgraded from 12.04.

Until 2 days ago, everything worked fine. Since then, when I've tried to watch videos online (YouTube) or play games online (embedded browser games, not MMO type games) while using the wireless connection, only a small part of it downloads. When I look at the network activity in the System Monitor, I see it stop receiving data, but it continues to send data at around 180 KB/s. If I go to the same website with my notebook connected to the router using an ethernet cable, the videos and games work just fine. Every other website I visit or download I start works perfectly using the wireless.

I can easily post results from terminal commands or screenshots of what's happening if needed. I updated the wireless driver not long after I got this notebook (late 2012) and I've never had a problem with it until now.

What could be happening?

---

### Post by JustSomeCanuck on 2014-06-16
Update: Telling YouTube to use HTML5 instead of Flash seems to have fixed the problem with the videos not loading, but the data sending through the network remains high. This is also slowing down the Internet connection when we try to use more than one computer (never a problem before). It's not a major problem, but it does bother me.

Could this even (dare I say it) be a virus? I've never seen anything like it, and a different notebook I have (also running Ubuntu) doesn't have the same problem.

---

### Post by JustSomeCanuck on 2014-06-16
Update: Telling YouTube to use HTML5 instead of Flash seems to have fixed the problem with the videos not loading, but the data sending through the network remains high. This is also slowing down the Internet connection when we try to use more than one computer (never a problem before). It's not a major problem, but it does bother me.

Could this even (dare I say it) be a virus? I've never seen anything like it, and a different notebook I have (also running Ubuntu) doesn't have the same problem.

---

### Post by JustSomeCanuck on 2014-06-28
Figured it out on my own...thanks to everyone who read this!

I should have installed Gnash earlier...

---

