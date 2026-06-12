---
title: "How to install Alternate Ubuntu9.04"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by bj218 on 2009-06-20
I want to upgrade (not reinstall)to Ubuntu9.04 from ver. 8.10. I downloaded "Ubuntu-9.04-alternate-i386.iso" and burned it to a CD. But now I can't figure out how to use the CD. Since I am new to Ubuntu can someone please explain in detail how to use this CD?

---

### Post by presence1960 on 2009-06-20
[https://help.ubuntu.com/9.04/installation-guide/index.html](https://help.ubuntu.com/9.04/installation-guide/index.html)

My opinion is you should do a clean install. If you peruse the forum you will notice that the vast majority of people complaining of problems after going to Jaunty 9.04 have done an upgrade rather than a clean install. For whatever reason the upgrade process isn't working as intended. But it is your choice. You can pay the piper now ( clean install) or pay the piper later (trobleshooting and likely reinstalling anyway)

---

### Post by Sef on 2009-06-20
There is less problems with a clean install.  If you do upgrade then uninstall any proprietary drivers you have and any third party software.

---

### Post by 3rdalbum on 2009-06-21
Don't listen to the naysayers, upgrading works every time for me.

It's easy to upgrade using the Alternate CD. Go to a terminal and navigate to the root of the CD (or open a terminal there using the Nautilus Open Terminal plugin). There should be a script called "cdromupgrade" there. Switch to root and run the script:

```
sudo su
./cdromupgrade
```

You will be walked through the process.

---

### Post by presence1960 on 2009-06-21
> **3rdalbum said:**
> Don't listen to the naysayers, upgrading works every time for me.

It's easy to upgrade using the Alternate CD. Go to a terminal and navigate to the root of the CD (or open a terminal there using the Nautilus Open Terminal plugin). There should be a script called "cdromupgrade" there. Switch to root and run the script:

```
sudo su
./cdromupgrade
```

You will be walked through the process.

I wouldn't say I am a naysayer. I am just stating the facts. Have you perused the Installation & Upgrade section since jaunty was officially released? There are a disproportionate number of threads concerning troubles during/after the upgrade process to 9.04. That does not mean every upgrade will have trouble- but the fact remains if one does a clean install it practically eliminates that chance of trouble occurring. Why chance it? In an effort to save doing some work now you may wind up doing a lot more later troubleshooting & maybe even reinstalling.

---

### Post by sadaruwan12 on 2009-06-21
> **presence1960 said:**
> I wouldn't say I am a naysayer. I am just stating the facts. Have you perused the Installation & Upgrade section since jaunty was officially released? There are a disproportionate number of threads concerning troubles during/after the upgrade process to 9.04. That does not mean every upgrade will have trouble- but the fact remains if one does a clean install it practically eliminates that chance of trouble occurring. Why chance it? In an effort to save doing some work now you may wind up doing a lot more later troubleshooting & maybe even reinstalling.

I totally agree with presence1960, I updated my system from 8.10 to 9.04 and bam every thing started to go wrong so I've to do a clean install so my advice to you do a clean install if you have your /home folder as a different partition then you don't have to worry about loosing your data. And it's like formating C:\ without removing the partitions in a windows environment.

---

### Post by nhasian on 2009-06-21
i upgraded several laptops from 8.04 to 8.10 and then to 9.04 by using the alternate CD.  I just put the alternate CD in the drive while i was at the ubuntu desktop.  it auto ran and asked if i wanted to upgrade to the new distribution.  I said yes, and it worked great for me each time.  it auto-disabled my 3rd party software sources so i had to go back in and re-enable them afterwards but everything worked fine.

---

### Post by kelvin spratt on 2009-06-21
Ugrading works every time for people that do not mix unofficial repros with the official ones that should be common sense,

---

### Post by k3lt01 on 2009-06-21
Upgrading by CD seems a rather long way round to upgrade if you already have an internet connection. Why download and then burn an entire CD if you just want to use it to upgrade your current install? Just use Update Manager to do the upgrade that way you upgrade with the current versions of all packages. If you upgrade by CD you will probably have to download a couple hundred MB of updates afterwards anyway.

---

### Post by 3rdalbum on 2009-06-21
I will agree with something said earlier: Remove your proprietary graphics card driver first. If you don't it's not the end of the world, you might just need to use the safe graphics mode to install a new graphics driver.

I've dist-upgraded from Breezy to Dapper, Gutsy to Hardy, Hardy to Intrepid on someone else's computer, and Intrepid to Jaunty on two different computers and it's been a cakewalk. The first dist-upgrade was on a different computer too.

EDIT:

> Upgrading by CD seems a rather long way round to upgrade if you already have an internet connection. Why download and then burn an entire CD if you just want to use it to upgrade your current install? Just use Update Manager to do the upgrade that way you upgrade with the current versions of all packages. If you upgrade by CD you will probably have to download a couple hundred MB of updates afterwards anyway.

Your fastest available internet connection could be one that you can't access on the target machine - for instance, if you're using a fast public wifi hotspot to download the alternate CD on a notebook, so you can update your desktop. Or, you might want to have a disc that can do most of the update for multiple machines on different locations.

If you're going to dist-upgrade, you might as well have a clean install disc too - so if you download the Alternate CD and use that as a source for upgrading, then the data you've downloaded is useful in both capacities.

Your ISP might have a free mirror of the disc images but not a full Ubuntu repository - so you can download 700 megabytes of Ubuntu packages that are needed for the upgrade without it counting towards your download quota. Sure, the Update Manager will still have to download a couple of hundred megabytes of things that aren't on the Alternate CD, but I'd rather lose 400 megs of download quota than lose 1.1 gigs of it!

---

### Post by k3lt01 on 2009-06-21
> **3rdalbum said:**
> Your fastest available internet connection could be one that you can't access on the target machine - for instance, if you're using a fast public wifi hotspot to download the alternate CD on a notebook, so you can update your desktop. Or, you might want to have a disc that can do most of the update for multiple machines on different locations.

If you're going to dist-upgrade, you might as well have a clean install disc too - so if you download the Alternate CD and use that as a source for upgrading, then the data you've downloaded is useful in both capacities.

Your ISP might have a free mirror of the disc images but not a full Ubuntu repository - so you can download 700 megabytes of Ubuntu packages that are needed for the upgrade without it counting towards your download quota. Sure, the Update Manager will still have to download a couple of hundred megabytes of things that aren't on the Alternate CD, but I'd rather lose 400 megs of download quota than lose 1.1 gigs of it!To an Aussie your comment makes perfect sense but thats because our internet access and speeds suck compared to the rest of he developed world. The OP is in California not Australia so I'm assmuning, maybe naively, that their internet access and speeds are superior to ours.

If a person is only upgrading 1 PC then it make sense to consider the option of upgrading via Update Manager. If the person, like many here, upgrades more than 1 PC then it makes sense to download and burn a cd, install, update, copy the cache of new files downloaded for the update, then use them to update other subsequent installs.

Personally I prefer a clean install but that is neither here nor there with upgrading because I do a full backup anyway.

---

### Post by bj218 on 2009-06-21
> **presence1960 said:**
> I wouldn't say I am a naysayer. I am just stating the facts. Have you perused the Installation & Upgrade section since jaunty was officially released? There are a disproportionate number of threads concerning troubles during/after the upgrade process to 9.04. That does not mean every upgrade will have trouble- but the fact remains if one does a clean install it practically eliminates that chance of trouble occurring. Why chance it? In an effort to save doing some work now you may wind up doing a lot more later troubleshooting & maybe even reinstalling.

1.Where & how do I find the "Installation & upgrade" section?
2.If I do a clean install how do I save my installed programs
and other data i have on 8.10?

---

### Post by presence1960 on 2009-06-21
[http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)

1. Installation & Upgrades is the second link under Main Support Categories.

2. If you have a separate /home partition most of your config files for software are there. When you install again choose "manual" option at the Prepare disk space window of the partitioner. Highlight your intended root partition, click edit partition and set partition type, use as (filesystem) and mountpoint (/). Then highlight your /home partition, click edit partition and set partition type, use as (filesystem) & montpoint (/home). **_Make sure the format box is unticked or you will lose your data if it is ticked for a format!_**. Continue with install and your separate home partition will be set and will work seamlessly for you. I would still back up all data!
If you don't have a separate home partition then you must back up and copy back after the install.

you can check this out for restoring your installed packages from the repositories : [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
unfortunately any software not from the repositories or any proprietary software must be reinstalled.

---

