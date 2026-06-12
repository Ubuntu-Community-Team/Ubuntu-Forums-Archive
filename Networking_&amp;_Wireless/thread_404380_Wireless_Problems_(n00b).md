---
title: "Wireless Problems (n00b)"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by zombiepunkcaptain on 2007-04-08
Hey Everybody,

First post - so rest assured the answers to my problems are most likely quite simple.


My friend, a veteran Linux user, has just helped me to install the latest version of kUbuntu. At this time I cannot tell you exactly what version it is, however 6.10 seems to be ringing a bell.


Anyway - the problem is that while **Linux recognises my Wireless Dongle it does not see any wireless networks.** He gave me a brief list of instructions, ensuring it was "extremely easy to fix", but it doesn't seem to have done the job.

He mentioned that** he may have set the Wireless up to "Monitor" rather "Managed"** and this is why it cannot see my wireless networks. The single prompt command he gave me is as follows:

**sudo iwconfig wlan0 grep 1 mode Managed**



I'd love to get this done before I go to sleep (Don't put off till tommorrow what you can do today, right?) and the Internet never sleeps so I thought that hopefully someone on here will have the answers.

I will regularly check the thread for the next 20 or so minutes...

Thankyou.

---

### Post by rolando on 2007-04-08
open up a terminal (not sure how to do in KDE). Have a look under accessories in the menu

type in

sudo iwconfig > iwconfig.txt

cut and paste the text file it makes in your home directory here

same for

sudo ifconfig > ifconfig.txt

:)

---

