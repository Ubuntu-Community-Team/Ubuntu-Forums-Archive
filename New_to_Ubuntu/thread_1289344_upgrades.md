---
title: "upgrades"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Calen_co on 2009-10-12
I am trying to raise my kernal from 8.04 to 9.04 and have tried running;
 [SIZE=2][FONT=Arial]apt-get update[/FONT][/SIZE]
[FONT=Arial] apt-get upgrade[/FONT]
[FONT=Arial][SIZE=2][FONT=Arial] apt-get dist-upgrade [/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial][/FONT][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][FONT=Arial]all from root and then rebooting, but I only get a message saying that 0 was updated and upgraded. Is there an additional command I am missing to actually install the upgrade?[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial][/FONT][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][FONT=Arial]Calen_co[/FONT][/SIZE][/FONT]

---

### Post by MelDJ on 2009-10-12
the kernel update will come up in update manager when it is updated by the devs.

---

### Post by achase79 on 2009-10-12
You may have to go to system -> administration -> software sources and select regular releases.  8.04 is a Long Term Release and will be defaulted to only upgrade to other long term releases.

---

### Post by MelDJ on 2009-10-12
> **achase79 said:**
> You may have to go to system -> administration -> software sources and select regular releases.  8.04 is a Long Term Release and will be defaulted to only upgrade to other long term releases.

if you want to upgrade the whole OS to 9.04. under the updates tab in software sources, change the release upgrade to normal. but you must upgrade to 8.10 then 9.04.

---

### Post by fbugnon on 2009-10-12
Actually, in despite of the name, the option dist-upgrade will "*intelligently handles changing dependencies with new versions*" and " *will attempt to upgrade the most important packages at the expense of less important ones if necessary*" (man pages), but it won't upgrade your distro into a new one (please correct me if I'm wrong, but that's what I could understand from man pages).

For this effect, try the Update Manager from you System > Administration menu,  You should se an option to upgrade to Ubuntu 9.04.

Be aware, however, that it can (and probably will) download many Mbs from the internet (maybe 400Mbs or more) and that Ubuntu 9.10 is going to be released shortly (couple 2-3 weeks) so you might want to wait a little longer and make a definitively one!

Or if you happen to have at hands a Ubuntu 9.04 alternate CD you can simply put it in (while Ubuntu is on) and it should automatically detects a new version and prompts you for the distro upgrade.

Hope it helps.  Good luck!

---

### Post by Calen_co on 2009-10-12
This is all good info and perhaps my being new to this is part of the problem. It sounds like you are saying that the upgrade (even in stages such as 8.10 and 9.04) are not readily available until a full release is in effect, am I correct in stating this? I have tried going through the GUI, but ultimately need to learn command line. I do have access to the 9.04 disk but am trying to do this on my own in an effort to learn.

---

### Post by mcduck on 2009-10-12
> **Calen_co said:**
> This is all good info and perhaps my being new to this is part of the problem. It sounds like you are saying that the upgrade (even in stages such as 8.10 and 9.04) are not readily available until a full release is in effect, am I correct in stating this? I have tried going through the GUI, but ultimately need to learn command line. I do have access to the 9.04 disk but am trying to do this on my own in an effort to learn.

The way to do a upgrade from one release to next using command line is to run the following command:

```
sudo do-release-upgrade
```

"apt-get dist-upgrade" doesn't upgrade to ext release, even though the name might sounbd like it would. What it does is that it upgrades your *current* distribution. f you wanted to do the upgrade to next release with apt-get you'd first have  to edit your sources.list to point to the new release's repsoitories, and *then* run "sudo apt-get update && sudo apt-get dist-upgrade".

It's also possible to start the graphical Update Manager manually from comamnd line with "-D"-option to tell it to offer release upgrade. If the Update Manager doesn't offer you the option to update to new release version even though it's already been released, check your update preferences, in that case they are most likely set to only offer updates to LTS versions. Simply changing the setting to allow all versions should cause the Update Manager to offer the update.

"apt-get update" updates the information about installed & available packages.

"apt-get upgrade" upgrades installed packages to latest available versions, and adds new packages if the upgrades for existing ones require that.

"apt-get dist-upgrade" behaves like "apt-get upgrade", but in addition is able to remove packages if necessary.

The Update Manager works like "apt-get upgrade", while upgrading in Synaptic behaves like "apt-get dist-upgrade".

---

### Post by Calen_co on 2009-10-12
Thank you - I will give this a try as soon as I get to that desktop.

---

