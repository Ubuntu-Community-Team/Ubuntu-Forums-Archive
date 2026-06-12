---
title: "Update from 8.04 or DL CD ?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by freeediver on 2010-10-24
All my important files are backed up.
Should I just click the 10.04 update button
or D.L. the CD and install from that?
How could or should this affect my existing files if I update or DL and install?
And as a fail safe how can I make a copy of 8.04 to re-install in case I have issues with 10.04?
Thanks

---

### Post by trikster_x on 2010-10-24
Save yourself a headache and download the CD.  I wish I had, since the upgrade took twice as long as running a fresh install.  As for making a copy of 8.04, I would suggest just making a small partition to run 10.04 off of until you get the bugs worked out, then delete 8.04 when you are comfortable with the stability of the new version.

---

### Post by Elfy on 2010-10-24
If you want to upgrade with the cd get the alternate.

If you want upgrade make sure that you have ubuntu-desktop installed. Remove all the 3rd party repositories you might have have amassed.

[I would also read the release notes - especially any known issues.]("http://www.ubuntu.com/getubuntu/releasenotes")

As far as backing up the install you could look at clonezilla - seems to be fairly commonly referred to here, not used it myself though.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by halj32 on 2010-10-24
> **trikster_x said:**
> Save yourself a headache and download the CD.  I wish I had, since the upgrade took twice as long as running a fresh install.  As for making a copy of 8.04, I would suggest just making a small partition to run 10.04 off of until you get the bugs worked out, then delete 8.04 when you are comfortable with the stability of the new version.
+1 for this option, it's a lot easier & a lot less hassle. Ive never had a successful upgrade. 
Dell I 1525 laptop + homebuilt 

 goodluck

---

### Post by freeediver on 2010-10-24
I've never used partitions before, will I be able to access files my existing 8.04 files?

---

### Post by Paqman on 2010-10-24
> **halj32 said:**
> Ive never had a successful upgrade. 


Just for balance, i've never had an unsuccessful one.

IMO if you're using a relatively standard machine that has software installed from proper repos and haven't been messing about compiling your own stuff you should have no problems upgrading. The upgrade process disables 3rd party repos before it begins, which used to be a source of problems in the past.

---

### Post by ieee488 on 2010-10-24
> **halj32 said:**
> +1 for this option, it's a lot easier & a lot less hassle. Ive never had a successful upgrade. 
Dell I 1525 laptop + homebuilt 

 goodluck

+1   as well

it will save you if anything goes wrong with the upgrade

---

### Post by waynefoutz on 2010-10-24
> **Paqman said:**
> Just for balance, i've never had an unsuccessful one.

IMO if you're using a relatively standard machine that has software installed from proper repos and haven't been messing about compiling your own stuff you should have no problems upgrading. The upgrade process disables 3rd party repos before it begins, which used to be a source of problems in the past.

Even a successful update is going to have some issues. Also 8.04 is a LOT different than 10.04, especially since 8.04 didn't have ext4 file system yet. 

I just did this upgrade on one of my machines, day before yesterday, just to see how it would go out of curiosity. It had a 2.5 year old install on it. It was successful, but it took over three hours. It also brought over a lot of baggage from the old OS, and the boot up time was painfully slow. I ended up formatting and installing fresh and the performance was far better after.

---

### Post by perspectoff on 2010-10-24
> **freeediver said:**
> All my important files are backed up.
Should I just click the 10.04 update button
or D.L. the CD and install from that?
How could or should this affect my existing files if I update or DL and install?
And as a fail safe how can I make a copy of 8.04 to re-install in case I have issues with 10.04?
Thanks

Re-install.

Serial upgrades from 8.04 to 10.04 are fraught with incompatibilities.

It's not so bad if you have/use only the minimal core Ubuntu installation, perhaps.

The problem is the associated programs/modules/apps. For example, the version of PostgreSQL is way different in Hardy than in Lucid, as is PHP, MySQL, and a myriad other programs.

These aren't exactly part of the Ubuntu core, but they get upgraded anyway.

If you've never had some of your databases stop functioning because Ubuntu has upgraded the version, consider yourself lucky. 

Heck even going from Karmic to Lucid isn't that easy for me because of this type of problem.

I have an old installation of Hardy I just looked at this week -- OMG that is different from Lucid! Not only that, the way I did things back then seems neolithic compared to today. (Having said that, Hardy was one of the most stable releases I have experienced in Ubuntu. Not all the apps I wanted were available for it, however). 

The hard part, then, is figuring out how to move stuff from the old installation to the new one.

Moving a website, for example, is not trivial. Moving databases, of course, is not at all easy, and installing old versions of a database in a new version of Ubuntu (in order to do a lateral move) can be a real chore.

Sometimes, if you are persistent, you can upgrade databases and things within Hardy up to the version found in Lucid (often has to be done manually) prior to a planned move. Then you can do the lateral move.

IMO that's the safest way to go, but also takes a lot of effort.

(Probably what a lot of users end up doing is running a virtual machine instance of their Hardy website within Lucid. That kind of defeats the purpose, but lets you get on with life.)

What I have found it necessary to do over the long run is to do an update every release of (K)Ubuntu of the entire system. If everything works, I stick with it. If not I stay back for a while.

That way I have at most two running versions of (K)Ubuntu -- the most current one and one that runs for sure with all my programs. With time, almost all of my programs get updated to be compatible with the newest (K)Ubuntu release (usually takes 3 - 6 months), and then I can convert completely to the newest release. 

Going all the way from LTS to LTS doesn't really work that well. The concept was ok, but Hardy is not updated in its modules all the way to what Lucid has, so transition is not really facile.

---

### Post by egalvan on 2010-10-24
OK, my nikle´s worth of opinions...ç


8.04 is LTS
10.04 is LTS

upgrades from LTS to LTS tends to be more stable, and less troublesome... not completely 100%, but the odds are better under LTS-LTS.

I upgraded fron 8.04 from 10.04 on a desktop, and so far so good.
I did what forest.pixie suggested and removed ALL except the standard Ubuntun repos, then re-enabled the ones that were still needed...
10.04 has two years of upgrades/updates that make it better... not all the repos/ppas will be needed.

I (of course) **backed up my data and /home before starting** the upgrade via Synaptic.
Took about the same time (probably less) as downloading7burning CD,
formatting (erasing) partitions, installing then updating.

As for this method taking longer than one fron an install CD...
of course it does, maybe, perhaps...
 it is downloading the files it needs, rather than downloading the install CD.
Take into account the time needed to get the install CD and add it to the total time, if you want to compare apples-to-apples.
Then remember that up-grading over the net gives you the latest files... the install CD may be more or less behind, so you may have up-dates to install immediatley after an install CD method.
:)


When the 10.04.1 re-pop came out, I downloaded live and alternative CD.
Tried on four different laptops, and failed on all four.
These are all running 8.04 in fine form.
Some work to do here, investigation and reading.

---

### Post by mikem94590 on 2010-10-24
I'd personally do a clean install; especially when your versions are that far apart.  Having said that, it's a lot easier if you have your /home partition mounted separately and can re-install the OS without touching all of your user data.  However, even if this were not the case, I'd still just go ahead and back-up all of your important data (if you have any) and do a clean-install.

---

### Post by trikster_x on 2010-10-24
> **freeediver said:**
> I've never used partitions before, will I be able to access files my existing 8.04 files?

Yes, you can access any partition on your hard drive and read/write to pretty much everything.  They mount up just as if you have another hard drive on your system.  The only filesytstems you can't write to are the HFS type filesystems.  But I have read that they are working on that as well, so I could be wrong.  

Partitioning is not hard, I juggle mine around all the time with no problems.  I would suggest you use gparted to make the empty space you will need for your install before you fire up the installer.  I have had a few problems with partitioning bugging out on me in the middle of an install, so now I just do all my partition work in gparted first, then install.  Other than that, just take your time and you should be fine.

---

### Post by ArgusVision on 2010-10-24
+1 for fresh install. Copy your home directory to another drive, install and copy the files to your new home directory.( be sure to to **sudo chown -R username:username /home/username** )
If you have room, make a new partition and copy your home directory to it, then make it your /home directory during the install.

---

### Post by freeediver on 2010-10-24
Ok
In the past I have just copied the individual
files over to my hard drive that I wanted to save.
How about a step by step for your procedure.
No one has ever shown me how to do a proper back-up
from Step one.
Thanks

---

