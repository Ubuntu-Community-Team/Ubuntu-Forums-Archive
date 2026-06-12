---
title: "Has anyone gotten the nvidia 173.14.15 driver working with Ubuntu"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-12-08
I am trying to get the nvidia 173.14.15 driver working with Ubuntu 8.10

I am able to load the driver, but nvidia-settings say's it is not running.

I need to know how you have gotten it running and hopefully a view of your xorg.conf to help me properly set it up.

Any help you could supply would be greatly appreciated.

Donnie

):P

---

### Post by gettinoriginal on 2008-12-08
Here are the google results, but it looks doubtful at this time:

[http://www.google.com/search?q=linux+installing+nvidia+173.14.15+driver+working+with+Ubuntu+8.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=linux+installing+nvidia+173.14.15+driver+working+with+Ubuntu+8.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Good luck :p

---

### Post by ellalan on 2008-12-09
> **alienexplorers said:**
> I am trying to get the nvidia 173.14.15 driver working with Ubuntu 8.10

I am able to load the driver, but nvidia-settings say's it is not running.

I need to know how you have gotten it running and hopefully a view of your xorg.conf to help me properly set it up.

Any help you could supply would be greatly appreciated.

Donnie

):P
Have you tried EnvyNG, I saw that version in mine.
I can tell you how I installed the v180.0
I have uninstalled everything begins with "nvidia" in synaptics.
Downloaded version 180.08 to my Desktop.
1.Ctrl+Alt+F1
2.sudo /etc/init.d/gdm stop
3.cd Desktop
4.sudo sh NVIDIA<Tab>
5.sudo reboot.
HTH.

---

