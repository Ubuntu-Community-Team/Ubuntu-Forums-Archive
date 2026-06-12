---
title: "How to auto-Mount a NAS network drive after booting up?"
date: 2015-04-09
forum: Networking &amp; Wireless
---

### Post by hhtmp88 on 2015-04-09
Hi all,

I have a Synology NAS, DS210j, with network name "hNAS", installed in the same LAN with a Celeron J1900 Tiny Computer.
Ubuntu Mate 14.10 is installed in that Tiny Computer.

After some setup in DS210j, Ubuntu can see "hNAS"
-> by double click on the icon of "hNAS", I can login into my hNAS user account, double click one of the folders, e.g. "mfy_sa"
-> mfy_sa will be mounted and an icon of it is placed on the desktop of Ubuntu Mate
-> however after reboot, mfy_sa disappears.

So my question is:
How to setup Ubuntu so that "mfy_sa" will be mounted automatically after boot up?

Thanks for any kind of help!

---

### Post by Morbius1 on 2015-04-09
Gigolo can be used to automatically mount the share at login - not boot: [http://ubuntuforums.org/showthread.php?t=1590825&p=9941016#post9941016](http://ubuntuforums.org/showthread.php?t=1590825&p=9941016#post9941016)

---

