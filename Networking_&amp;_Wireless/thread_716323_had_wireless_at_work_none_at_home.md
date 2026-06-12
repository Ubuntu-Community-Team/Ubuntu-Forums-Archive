---
title: "had wireless at work none at home"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by paulzaplitny on 2008-03-05
i am running gutsy i have a linksys wmp54g which worked right out of the box no problem. i intalled it at work and it connected fine. just brought computer home and i see my network but it wont connect to it weird any suggestions?? i am very new to linux.

---

### Post by schmildo on 2008-03-05
When you say it worked at work, were you using linux or windows at the time?

Find out what sort of wireless router you are using at home and post that here.

Find out what sort of wireless security settings your home wireless router is using and post that also.

For example I had the same problem as you a couple of weeks ago, (with another version of linux) I was using a more secure method of communication, that for some reason other people weren't using very much, but I got it working.

Also type some commands in the console to help us figure it out such as:

sudo ifconfig -a

sudo iwconfig

sudo lshw -C network

post the results of these three comands.

One you post the results of this i imagine someone will figure out the issue for you very quickly.

Good luck!

------- If you dont get an answer from anyone and you're keen to give it a go; i've found a website that might solve your problem.

[http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/](http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/)

---

