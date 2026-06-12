---
title: "Need help with upgrade to 9.10"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by LoganS on 2009-04-24
I have already posted the following message in the Post section

[B]Upgraded from 8.10 by way of package manager. Did update then upgrade. Once or twice had to reboot during download. Can not get 9.04 to run. Had to get online using my installation DVD for 8.10. I suspect the problem is corruption in GRUB files but am not sure. Have tried to reload GRUB files several times after hitting escape button and being presented with menu.
[/B]

I need help as this is my first time doing an upgrade. As Robert Heinlein wrote "You can not pay it back but you can pay it forward"  And I will do that

Thanks very much

---

### Post by DGortze380 on 2009-04-24
I suggest you back up your personal files, download a fresh 9.04 (9.10 is not out yet) cd, and do a clean install. I also suggest you create a separate home partition for future upgrades. You'll need to select manual partitioning, reformat your current install partition, create a new partition for /home and select the mount points.

Alternately, you can attempt to upgrade via the update manager, in my experience this has about a 50/50 chance of being totally successful.

---

### Post by LowSky on 2009-04-24
rebooting during the download is a very, very, very, very, very (I hope you get the idea) thing to do..

---

### Post by bodhi.zazen on 2009-04-24
Upgrade to 9.10 ???

Ubuntu numbers it's releases by year.month , so it is not 9.10 yet ;)

Upgrade to 8.10 or 9.04 ?

If the upgrade process wa interrupted by reboots it is likely your installation is corrupt.

boot a desktop CD or DVD into the version you are upgrading to to make sure you do not have a hardware problem.

---

### Post by denphi03 on 2009-04-24
I have also been having an issue with the upgrade through the update manager.

same type of issue, was installing the upgrade and it only got so far then it froze.

had to restart (since i dont know what the ubuntu equivalent of ctrl+alt+del is)

restarted and waited a super long time for it to set up the upgrade and then after waiting a few hours while the packages were downloading it gave me an error.

guess i'll need to try and reinstall via cd instead of upgrading.

....sounds like the thread starter should consider the same

---

### Post by mhh91 on 2009-04-24
> **bodhi.zazen said:**
> Upgrade to 9.10 ???

Ubuntu numbers it's releases by year.month , so it is not 9.10 yet ;)

Upgrade to 8.10 or 9.04 ?

If the upgrade process wa interrupted by reboots it is likely your installation is corrupt.

boot a desktop CD or DVD into the version you are upgrading to to make sure you do not have a hardware problem.

maybe he's ahead of his time :lolflag:


OP: make sure you got the title right next time :)

---

### Post by bodhi.zazen on 2009-04-24
While the upgrade process usually goes smoothly, keep in mind :

1. The servers get hammered the first few days following a release. Perhapsy wait a few days ?

2. The upgrade process is NOT foolproof and is a major change in any OS. Always back up first and be prepared to re-install.

3. If the upgrade process is interrupted for any reason (power loss, etc) the system is often broken beyond easy repair as it is often a mix of old and new packages.

---

### Post by LoganS on 2009-04-25
Thanks for the input.  My Bad on the title.  I believe the best is just to install 9.04 from a CD.  Any thoughts?

Thanks

---

### Post by philinux on 2009-04-25
> **LoganS said:**
> Thanks for the input.  My Bad on the title.  I believe the best is just to install 9.04 from a CD.  Any thoughts?

Thanks

Yep good idea. And put home on it's own partition. You need to select the manual option. Backup anything important first.

---

### Post by LoganS on 2009-04-25
Thanks Philinux Is there any online information about putting home on its own partition or should it be self explanatory?

Thanks

---

### Post by DGortze380 on 2009-04-25
> **LoganS said:**
> Thanks Philinux Is there any online information about putting home on its own partition or should it be self explanatory?

Thanks

I think this is for an existing install, but it's very similar on a new install.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

