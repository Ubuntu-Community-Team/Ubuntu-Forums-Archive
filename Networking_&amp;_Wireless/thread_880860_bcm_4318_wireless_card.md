---
title: "bcm 4318 wireless card"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by cc8balla on 2008-08-05
After extensive searching on here, and on the internet, I've finally resigned to asking. I have recently switched from Ubuntu 8.04 to Kubuntu 8.04, as I prefer KDE to GNOME. 

Now, I cannot get my wireless card to be recognized, and I do not know why, as it worked fine in Ubuntu. Any help on how to get it working in KDE?

---

### Post by Ayuthia on 2008-08-05
> **cc8balla said:**
> After extensive searching on here, and on the internet, I've finally resigned to asking. I have recently switched from Ubuntu 8.04 to Kubuntu 8.04, as I prefer KDE to GNOME. 

Now, I cannot get my wireless card to be recognized, and I do not know why, as it worked fine in Ubuntu. Any help on how to get it working in KDE?

EDIT:  I just realized that my original question was answered in the title.  You will need to enable the card by going into System->Administration->Hardware Drivers which will help install the firmware for it.  However, you can go the ndiswrapper route.  Here is one additional link for ndiswrapper that works fairly well:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by cprofitt on 2008-08-05
Here are some resources for you to use to get your card working

[https://answers.launchpad.net/ubuntu/+question/35296](https://answers.launchpad.net/ubuntu/+question/35296)

[http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/](http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/)

[http://www.linuxquestions.org/questions/ubuntu-63/problem-with-b43-fwcutter-on-hardy-heron-638375/](http://www.linuxquestions.org/questions/ubuntu-63/problem-with-b43-fwcutter-on-hardy-heron-638375/)

Try seeing if you have a restricted driver that you can load first... as that would be the easiest.

---

