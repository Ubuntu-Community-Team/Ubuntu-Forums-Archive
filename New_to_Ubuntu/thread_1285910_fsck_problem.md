---
title: "fsck problem"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by chayanman on 2009-10-08
hi guys,
i've got an problem for which i can't open my pc with ubuntu 8.10.it shows 
**unclean shutdown,run fsck manually (without -a or -p option).fsck died with exit status 4**.then it wants root password,when i give it it shows **incorrect password**.what can i do to fix it? thnx in advance....

---

### Post by LewRockwell on 2009-10-08
use a *nix distro LiveCD to run fsck manually

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

.

---

### Post by kappa962 on 2009-10-08
I've had this problem, and I'm fairly certain I was able to get to a prompt and fsck by just hitting enter when prompted for the password.

---

### Post by tarps87 on 2009-10-08
> **chayanman said:**
> hi guys,
i've got an problem for which i can't open my pc with ubuntu 8.10.it shows 
**unclean shutdown,run fsck manually (without -a or -p option).fsck died with exit status 4**.then it wants root password,when i give it it shows **incorrect password**.what can i do to fix it? thnx in advance....

By the root password it usually means the password of the first user, is this what you are trying to use?

Failing try booting into recovery mode or use a bootable distro as LewRockwell mention. If you installed Ubuntu using the live cd this will do.

If you can log on type this
[code]fsck /dev/*diskItfailedOn*[code]

or if you are using the live cd use sudo

[code]sudo fsck /dev/*diskItfailedOn*[code]

---

### Post by ikisham on 2009-10-08
Before I installed Karmic I tried to upgrade from Jaunty (I had some unnofficial packages installed) and it wouldn't boot. It kept givin' that error like yours and there was no means to log in (whatever typed or not typed gave 'wrong password').
I think I ran fsck from another partition with another Linux and when rebooted it gave me a 'Kernel panic'.

My former install was already somewhat messed up (it was from a Crunchbang install and had PPA's enabled in the sources.list) so I didn't think twice, downloaded 9.10 beta and I'm happy.** it may work well for some and not for others*

(just saying it may not be easy, but if you need, back-up your data and reinstall)

---

