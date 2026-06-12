---
title: "how to update to 8.10"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by monolux on 2009-02-13
I'm trying to update my ubuntu to 8.10 but i cant figure out how. Can anyone help me?

---

### Post by Muffinabus on 2009-02-13
You'll have to go into system > administration > software sources, I forget which tab it's on, but you'll see a drop down box on one of them that allows you to specify that you want to be able to upgrade to the next stable release.  You can also download the 8.10 (alternate cd?) and upgrade via that as well.

And you may want to backup important files before you do upgrade, some people experience some system instability when doing so.

---

### Post by drs305 on 2009-02-13
You will need to tell us which version you are trying to update from. 

The easiest way if the versions are compatible is to just go to System > Administration > Update Manager and click on the link in the upper right corner if it says a newer version is available. This is called a dist-upgrade.

You can also install via the new version's LiveCD but you will lose your customized settings unless you have a separte /home partition.

No matter how you decide to upgrade, make backups of any important data on the partitions you will be working with during the upgrade.

Links Added:
[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html]("http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html")

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by Muffinabus on 2009-02-13
His profile says he's on 8.04, so I just assumed that was correct.

---

### Post by johnjohn2 on 2009-02-13
> **Muffinabus said:**
> You'll have to go into system > administration > software sources, I forget which tab it's on, but you'll see a drop down box on one of them that allows you to specify that you want to be able to upgrade to the next stable release.  You can also download the 8.10 (alternate cd?) and upgrade via that as well.

And you may want to backup important files before you do upgrade, some people experience some system instability when doing so.

What i would suggest to do is completely reinstall and if you have a separate partition for the home directory all your settings would be kept

---

### Post by bodhi.zazen on 2009-02-13
> **monolux said:**
> I'm trying to update my ubuntu to 8.10 but i cant figure out how. Can anyone help me?

complete instructions are on the wiki :

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by cycloh on 2009-02-13
Can I partion a HD fat32 and ext3 using partion majic to install Ubuntu and xp?

---

### Post by bodhi.zazen on 2009-02-13
> **cycloh said:**
> Can I partion a HD fat32 and ext3 using partion majic to install Ubuntu and xp?

I am not sure about partition magic, you can certainly do it with gparted from the Ubuntu Live CD.

---

