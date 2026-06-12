---
title: "Setup dual boot with XP in current system configuration"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by jmendez2 on 2009-01-07
Hi everybody,

I currently have Dapper installed on my Dell Inspirion E1405.  I want to set this laptop up as dual boot with XP.  I just need some advice doing this.  

Attached is the current disk partition.  On it there is an "unallocated" partition with 7.17 GB of space.  Is this free space that my system is not using and would it be safe to install XP in this partition?

I am asking this question because I have decided to use this guide to help me in seting my dual boot system:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

Has anyone used the guide above with Dapper?  If so, do you have any changes or advice to make things flow smoothly?


Thank you all for the advice,

---

### Post by Captain_tux on 2009-01-07
I think that's too small a partition to efficiently run XP... I mean, you could, but it'd be **really** sluggish.

And I know **Dapper** is still supported... but why not upgrade to at least 8.04?

---

### Post by egalvan on 2009-01-07
> **Captain_tux said:**
> I think that's too small a partition to efficiently run XP... I mean, you could, but it'd be **really** sluggish.

And I know **Dapper** is still supported... but why not upgrade to at least 8.04?

First part...

I run dual-boot XP with average partition sizes of 6-8g, depending on how much I strip out from the install...
No "sluggish" behaviour noted.
Note,
none of them has less than 512M RAM.
all have fixed swap file sizes ( approx 768M ).
they all share an ext2 partition for excess data.


Second part...

Good question... why are you sticking with Dapper?
Compatibility issues? Resources?

ErnestG

---

### Post by jmendez2 on 2009-01-07
That is a good question.  Is there a link someone can provide me on how to upgrade to 8.04?

Also, I would still like to setup my dual boot.

---

### Post by Learner Driver on 2009-01-07
Here is a link to Ubuntu downloads:

_[http://us.releases.ubuntu.com](http://us.releases.ubuntu.com)_

Ubuntu 8.10 is the latest version.

If you are planning to dual boot Win XP and Ubuntu 8.10, you should choose the &#8220;Alternate Install CD&#8221; download option for Ubuntu 8.10.

---

### Post by Captain_tux on 2009-01-07
> **egalvan said:**
> First part...

I run dual-boot XP with average partition sizes of 6-8g, depending on how much I strip out from the install...
No "sluggish" behaviour noted.
Note,
none of them has less than 512M RAM.
all have fixed swap file sizes ( approx 768M ).
they all share an ext2 partition for excess data.



That there ain't no normal installation, hoss... know what I mean?

;)

---

### Post by egalvan on 2009-01-14
> **Captain_tux said:**
> That there ain't no normal installation, hoss... know what I mean?

;)

So, what is "un"-normal about them? :)

I use Parted Magic LiveCD to partition the drive, giving XP approx 8G.

I use a XP install CD, install to first partition...

then start up XP,

then kill "System Restore" and  "Hibernate",

then set swap file to approx 768M.

Defrag a couple times, rebooting between them,,,

then if needed/wanted, reduce the XP partition size...

I've got XP installed onto a 2G partition, using XP-Lite...
that was a bit more work...

---

### Post by zvacet on 2009-01-14
@ **jmendez2**

With [Gparted live Cd]("http://gparted.sourceforge.net/") you can make your Windows partition bigger  (10GB) and after that install Windows.You will need to [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")When you done it look [here]("https://help.ubuntu.com/community/HardyUpgrades") for upgrades to Hardy.Before you do upgrae maybe you want to make separate home partition.If yo decide to do that follow [this]("http://www.psychocats.net/ubuntu/separatehome") guide.For upgrading to Hardy I will use alternate CD.

---

### Post by jmendez2 on 2009-01-14
I've read in a couple places that if the partition named 'C' is not given to windows then some problems will arise.  How can I make sure that windows gets the partion C?  Is that something I can do in ubuntu or during the windows installation process?

Thanks!

---

