---
title: "2 instances of linux in grub"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by ububeginner on 2010-10-16
Hi all.
I installed Ubuntu 10.10 to dual boot with win 7 a couple of weeks ago. So far its going good but I do have a couple of questions.

1. My grub menu shows 2 instances of Ubuntu.
At first my Grub menu showed "Ubuntu, with linux 2.6.32-24 generic" and its recovery mode, but then all of a sudden (probaly after an update) it added "Ubuntu, with linux 2.5.32-25 generic" and its recovery mode. Why? Do I still have an old unupdated version of ubuntu lurking in the background that I need to get rid of? If so, how do I do that?
 
2.KDE not uninstalling correctly
I tried installin KDE but then decided it I liked gnome better. After uninstalling KDE with

sudo aptitude remove kubuntu-desktop

it still went to the KDE login screen at startup and it is still showing me a blue screen which says Kubuntu at log out. 
Do I still have some leftovers form KDE on my system? how do I get rid of them?
Thanks

---

### Post by wilee-nilee on 2010-10-16
The lines in grub are kernels, not separate OS. Generally it is advised to have at least two; one the oldest would be a back up.

This site has the whole desktop list in a row for removal and installation, always check that your using the correct distro.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ububeginner on 2010-10-16
Thanx for a quick reply,

That link was helpful and now I'm back to a pure gnome state

---

