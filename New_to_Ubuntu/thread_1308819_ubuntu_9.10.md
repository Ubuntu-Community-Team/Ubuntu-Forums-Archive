---
title: "ubuntu 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by joe2005 on 2009-10-31
I have ubuntu 9.04 installed along with windows rc and windows xp as triple boot.Now I have also downloaded ubuntu 9.10 from torrents.How do I upgrade from iso?

---

### Post by Zheldon on 2009-10-31
9.04 should allow you to upgrade to 9.10.  Check your update manager.  For me it was near the top but outside of the list.

---

### Post by nelamvr6 on 2009-10-31
You might want to consider a more descriptive title for your thread if you really want help...

Just saying...

---

### Post by Nburnes on 2009-10-31
Your normal update manager should just show 9.10 as an available upgrade.

---

### Post by undecim on 2009-10-31
Since 9.10 includes an upgrade of the default filesystems, you should backup your files and do a fresh install. The speed boost from the new ext4 filesystem is worth it!

You may be able to copy any files you want to keep to one of your windows partitions.

Or, if you have a separate partition for /home/ you can just do a fresh install, as long as you make sure not to format your home partition.

If you just want to upgrade, just use your update manager to do so.

---

### Post by frt975 on 2009-10-31
usealy you run sudo apt-get update && sudo apt-get upgrade. there is a way to update from cd, but i don't know it

---

### Post by joe2005 on 2009-11-01
I am sorry for not having explaned my problem in a better way.i want to upgrade from 9.04 to 9.10 using the cd burnt from downloading torrent.Is it possible?

---

### Post by stinger30au on 2009-11-01
i belive you can if oyu use the alternate cd


the other way is to burn 9.10 to cd

then start 9.10 and once its started, wipe out the current linux partitions using gparted, but only after backed up your data of course

then tell ubuntu to install the space left on the hdd where ubuntu once was

---

### Post by Prince.Paul.K on 2009-11-01
> i belive you can if oyu use the alternate cd

**Yes, for upgrade you have to use alterante CD.**

You can have a fresh install of 9.10 with the CD you have burnt.

---

### Post by shafin on 2009-11-01
upgrading with alternate CD is not a wise choice, in my experience, you'll still end up downloading packages. Best choice would be upgrading via update manager. Even if it crashes, the progress is saved, so you'll not lose anything.

---

