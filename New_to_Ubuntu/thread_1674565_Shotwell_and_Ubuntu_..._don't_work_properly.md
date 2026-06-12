---
title: "Shotwell and Ubuntu ... don't work properly"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by jermza on 2011-01-24
I have imported a bunch of pictures into Shotwell. 

When I click on "show in file manager", it opens the folder where the pictures are located, but it doesn't highlight the picture I asked it to show me.  It simply opens the folder in which the pictures are located.

I understand "show in file manager" to actually show me the image in the file manager.

Is there a fix for this?

---

### Post by NightwishFan on 2011-01-24
I recall someone asking this question a bit ago. I think the answer is "no there is not currently a way". This being open source though you can code it or petition the developers about it. :)
[http://yorba.org/shotwell/](http://yorba.org/shotwell/)

---

### Post by jermza on 2011-01-24
Thanks.  (Unfortunate.)

How do I upgrade Shotwell?  I see that the latest version is 0.8-something, and I have 0.7-something.  But, when I "mark for upgrade" in Synaptic, there are no upgrades available.

I even used:

sudo apt-get upgrade

---

### Post by NightwishFan on 2011-01-24
I will explain some quick basics about that. Ubuntu does not use a rolling model of software. It keeps the version the same of any particular software such as Firefox 3.5 or Banshee 1.6 and only accepts bug fix releases. Every 6 months there is a new release of Ubuntu with more modern software. This sounds limiting but it is actually quite flexible as it allows you to guarantee that a particular feature or program will be available and working for a period of time (at minimum 1.5 years).

To get a new version of Shotwell you can install it yourself using Yorba's official Ubuntu repository. To do so open a terminal and simply run this command:
```
sudo add-apt-repository ppa:yorba/ppa && sudo apt-get update && sudo apt-get upgrade
```

Please have fun! :)

Edit: If you have Ubuntu 10.04 (Lucid) you will only be able to get Shotwell 0.7.2

---

