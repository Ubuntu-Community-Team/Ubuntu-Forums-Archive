---
title: "Upgrading ubuntu"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by SegaFan on 2009-06-23
I don't know if this should go in absolute beginner because I've been using Ubuntu for quite some time and know my way around, mostly, but this is an absolute beginner's type of question I really should know the answer to but don't. I thought the answer would benefit beginners more than anyone else.

How do you upgrade to the latest version of Ubuntu?

I'd stopped using this PC for a while and it's gone horribly out of date; I'm still running Gutsy Gibbon. Now I can't use it anyway because I can't download/install any packages because, I assume, it's no longer supported.

Also, is upgrading anything to worry about, i.e. is there any risk of losing anything that I should backup beforehand?

---

### Post by Sef on 2009-06-23
**Back up** your** data** before upgrading or doing a clean install.  There are no 100% guarantees that all will go well.  I would do a clean install of jaunty, but run the live cd for a while and see if it works well with your system.

---

### Post by SegaFan on 2009-06-23
Well that's kind of the problem; I don't really want to do a clean install if I can help it because things didn't work smoothly straight away when I first installed Gutsy, it took a lot of effort to get everything working and now I need it to just work.

What about doing the upgrade to 8.04 using the update manager? And is there any way to upgrade to 9.04 without doing a clean install?

---

### Post by Sef on 2009-06-23
There is a method to upgrade using the [alternate cd]("https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD").

---

### Post by SegaFan on 2009-06-23
Thanks Sef,

I see from the upgrade notes that I could upgrade directly (using the update manager) from 7.10 to 8.04, from 8.04 to 8.10, and from 8.10 to 9.04 (but not directly from 7.10 to 9.04).
[https://help.ubuntu.com/community/UpgradeNotes#From%208.04%20LTS%20to%208.10](https://help.ubuntu.com/community/UpgradeNotes#From%208.04%20LTS%20to%208.10)

That looks like a straight forward, if a little long, way of doing things but is it wise to upgrade like that?

Also, let's say I just decide to do what looks like an easy upgrade to 8.04 LTS using the update manager and stick with that. How risky is it to do an update like that in terms of risk of loss of data and things going wrong? Will my settings, installed packages and everything like that be preserved? Or pehaps I'm worrying too much.

---

### Post by halitech on 2009-06-23
before doing any updating or upgrading, change your repo list and update. The archives aren't gone, just the address has been changed.

```
gksudo gedit /etc/apt/sources.list
```
change archive.ubuntu.com to old-releases.ubuntu.com/ubuntu
then run```
sudo apt-get update && apt-get upgrade
```
then you should be able to change your sources.list to whatever 8.04 uses and run
```
sudo apt-get dist-upgrade
```

** I've never done this in Ubuntu but it should work, YMMV

---

### Post by Mark Phelps on 2009-06-23
> **SegaFan said:**
> Or pehaps I'm worrying too much.

Personally, don't think it's even possible to worry "too much" ...

A reasonably good way to see what will work and what won't with an upgrade is to boot from the LiveCD for that version and see what works and doesn't.  Of course, any customizing you did won't work, but the basic stuff will.  You might be surprised by what works by default in the newer versions.

Also, if you're really worried about problems with an update, suggest you do a backup of your existing installation to an external drive before you do the update. I use P.I.N.G (Partimage Is Not Ghost), but there are others as well.  You want something that will allow you to burn a boot CD and restore from saved image files.

That way, if an upgrade leaves you with unsolvable problems, you can get a working system back in 15 minutes instead of several hours.

---

### Post by Celauran on 2009-06-23
> **SegaFan said:**
> 
I see from the upgrade notes that I could upgrade directly (using the update manager) from 7.10 to 8.04, from 8.04 to 8.10, and from 8.10 to 9.04 (but not directly from 7.10 to 9.04).
[https://help.ubuntu.com/community/UpgradeNotes#From%208.04%20LTS%20to%208.10](https://help.ubuntu.com/community/UpgradeNotes#From%208.04%20LTS%20to%208.10)

That looks like a straight forward, if a little long, way of doing things but is it wise to upgrade like that?


Upgrades have a reputation of being pretty catastrophic and you're looking to do three back to back. In this case, I think a clean install is really the best way to go. In the end, I expect it will save you a ton of grief.

---

### Post by Therion on 2009-06-23
> **Celauran said:**
> In this case, I think a clean install is really the best way to go. In the end, I expect it will save you a ton of grief.
Agreed... Well put.

---

### Post by LewRockwell on 2009-06-23
> **SegaFan said:**
> I don't know if this should go in absolute beginner because I've been using Ubuntu for quite some time and know my way around, mostly, but this is an absolute beginner's type of question I really should know the answer to but don't. I thought the answer would benefit beginners more than anyone else.

How do you upgrade to the latest version of Ubuntu?

I'd stopped using this PC for a while and it's gone horribly out of date; I'm still running Gutsy Gibbon. Now I can't use it anyway because I can't download/install any packages because, I assume, it's no longer supported.

Also, is upgrading anything to worry about, i.e. is there any risk of losing anything that I should backup beforehand?

I think you should burn a live-run CD and make sure it works on your system before you do **ANYTHING** else.

---

### Post by LewRockwell on 2009-06-23
> **SegaFan said:**
> Well that's kind of the problem; I don't really want to do a clean install if I can help it because things didn't work smoothly straight away when I first installed Gutsy, it took a lot of effort to get everything working and now I need it to just work.

What about doing the upgrade to 8.04 using the update manager? And is there any way to upgrade to 9.04 without doing a clean install?

If the live-run works ok with your older(now than it was before) equipment then you will have a joyous time doing a clean install

after your back-ups are done, of course

also, you might take the time to DBAN or KillDisk the drive before repartitioning and reinstalling

and you might even like [http://www.partedmagic.com/](http://www.partedmagic.com/) which, as of it's last release, now has clonezilla built-in!

and if you've got a desktop then you might do a little internal cleaning like this:

[http://ubuntuforums.org/showpost.php?p=7493629&postcount=15](http://ubuntuforums.org/showpost.php?p=7493629&postcount=15)

---

