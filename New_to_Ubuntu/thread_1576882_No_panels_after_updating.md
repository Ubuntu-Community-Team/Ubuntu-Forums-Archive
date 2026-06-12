---
title: "No panels after updating"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by lonewolfandcub on 2010-09-18
Hi there, I am presently re-installing Ubuntu on a new(used) PC desktop. After doing the initial installation, I downloaded the updates and installed them using the update manager. After rebooting  I got two error messages, the first was about the configuration server " /usr/lib/libconf2-4/gconf-sanity-check-2 exitedwith status 256", and the other message reads '' Nautilus could not create folders: /home/(my username)/desktop,/home/ my username/. nautilus". After that I get the background screen as usual but I do not have the panels above and below, in other words, no access to the applications menus. Even if I right-click, nothing happens. Ubuntu works fine from the CD and from what I am presently running, my USB stick, as well as on an ancient PII running at 350mhz. My new computer is a PIV running at 3.0Ghz with a tandem Windows XP/Ubuntu 9.1. What happenned?

---

### Post by Gone fishing on 2010-09-18
I think this maybe a bug?

I'd first try to make another account from a terminal alt control F2 

sudo useradd -m username then sudo passwd username

Can you then login?

You may also be able to fix the problem with 

sudo chmod 775 /etc/gconf/gconf.xml.system

have a look at [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

---

### Post by lonewolfandcub on 2010-09-18
Thanks for the tip, I checked it out. most of it seems dated  2008, therefore one would conclude that the bugs should have been repaired/corrected. I think what I'll do is simply reload from my original CD and install the earlier updates and try to avoid anything that resembles the grub... I sure wish I knew basic programming, maybe I could debug a little better myself. Thanks for the help.
](*,)

---

### Post by Gone fishing on 2010-09-19
You would think... but? However. chmoding that directory wont make things worse, 755 are the permissions are on my system although the directories empty.

The first suggestion was just to see if you account has a problem. I don't think you have a grub problem, I think a gnome problem. You could backup /home and install 10.04

---

