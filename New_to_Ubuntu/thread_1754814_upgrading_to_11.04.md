---
title: "upgrading to 11.04"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by sibhi on 2011-05-10
I am trying to upgrade from maverick to natty. I could not get it in update manager. I did everything given. Like selecting normal releases in settings tab of update manager. But I could not see the upgrade prompt. Kindly suggest me what to do.

---

### Post by dniMretsaM on 2011-05-10
You have to download the 11.04 .iso and burn it to a CD (like you were installing it for the first time). When you come to the menu asking what you want to do (partition, fresh install, etc.) there will be an option to upgrade from 10.10 to 11.04. Select that and you're on your way. Just be warned that updating tends to cause problems. I personally would do a fresh install. If you do that, just make sure to back up your data.

---

### Post by Frogs Hair on 2011-05-10
Backup what you want from your current installation and do a clean installation if possible . I'm also gun shy when it comes to upgrades.
If you decide to upgrade read this.[https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)

---

### Post by tkelito on 2011-05-10
I would also tend to agree with the fresh installation.  My 10.10 -> 11.04 upgrade didn't go all that smoothly.  

Make sure to backup your data for a fresh install, though I sure you run daily backups anyways (I hope..).

---

### Post by jeremychristopher on 2011-05-11
Hi!
If you want to install 11.04 on your computer, you really need to download the ISO file from Ubuntu. I did an upgrade earlier this month straight from Ubuntu 10.10. But it turned out to crash the system. It is not actually advisable to do upgrades from old versions. It is recommendable though to do a fresh install to avoid any conflicts with the settings defined in the previous versions. The possibility of installation errors are slim in this method.

---

### Post by sibhi on 2011-05-16
how to upgrade ubuntu online through command prompt. please let me know

---

### Post by Hedgehog1 on 2011-05-16
If you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by fritz269 on 2011-05-16
Here's what I did

**Get Ubuntu 11.04**

 **Upgrading from Ubuntu 10.10**

 To   upgrade from Ubuntu 10.10 on a desktop system, press Alt+F2 and type  in  "update-manager -d" (without the quotes) into the command box.  Update  Manager should open up and tell you: New distribution release  '11.04' is  available. Click Upgrade and follow the on-screen  instructions. 

[http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1)

download takes about an hour and install about another but it worked for me

---

