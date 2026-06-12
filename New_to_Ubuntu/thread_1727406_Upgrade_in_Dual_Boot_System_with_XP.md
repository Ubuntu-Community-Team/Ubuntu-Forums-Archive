---
title: "Upgrade in Dual Boot System with XP"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by dkanstro33 on 2011-04-12
I currently have an old version of Ubuntu (9.04) installed on my laptop as a dual boot with Windows XP.  I want to upgrade to either 10.04 or 10.10.  I just wondered before I got started whether there would be a problem with upgrading in this dual boot situation, or should I just download the new version, burn to a CD and do the install.  I know that with a several version upgrade I need to save all my data and settings to reinstall after the upgrade.

---

### Post by rosencrantz on 2011-04-12
No, I don't think so. You will, of course, get a new Grub in the process, but it should detect the installed Windows automatically.
You should keep backups of your personal data on all partitions (also on NTFS partitions), but that's good data handling practice anyway. The risk of something happening to your Windows install is very low.
You might have to do a multi-step upgrade (I don't know whether 9.04 is recent enough to do it directly). 
9.04 to 10.04 seems to be easy.
[http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directl](http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directl)

---

### Post by HermanAB on 2011-04-12
Well, I learned years ago, never to do an upgrade of either Linux or Windows.  It may actually work these days, but re-installing from scratch is always much easier and faster.

---

### Post by seawolf167 on 2011-04-12
> **HermanAB said:**
> Well, I learned years ago, never to do an upgrade of either Linux or Windows.  It may actually work these days, but re-installing from scratch is always much easier and faster.

+1 for this. Even if it does appear to work, it seems like the majority of the time there is something that won't and you won't find it out until you actually need to use it. 

Ubuntu is super fast and easy to install anyways (especially if you have a separate /home partition).

As usual, make a backup before just as an insurance policy (IMO [Clonezilla ]("http://www.clonezilla.org")is the best), then install a clean new version.

---

### Post by wolfen69 on 2011-04-12
> **hermanab said:**
> well, i learned years ago, never to do an upgrade of either linux or windows.  It may actually work these days, but re-installing from scratch is always much easier and faster.

+1000

---

### Post by rosencrantz on 2011-04-12
Well, I would definitely second that on OpenSuSE (not to mention Windows), but Ubuntu upgrades tend to work. It also spares me from having to re-install every bit of extra software I'm running.

---

