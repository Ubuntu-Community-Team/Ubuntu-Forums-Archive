---
title: "best way to upgrade?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-08-09
I'm sure this has been addressed but apparently I'm not entering the right combo  of words in the search. A google search netted me conflicting info, so I thought I'd better ask here to be certain.  I am running hardy so I know that I'd need to update to 8.10 before going to jaunty but.. is it a bad idea to upgrade instead of doing a clean install? I hate to lose all the stuff I have so far. 

mystmaiden

---

### Post by callan79 on 2009-08-09
> **mystmaiden said:**
> is it a bad idea to upgrade instead of doing a clean install? I hate to lose all the stuff I have so far. 


Hi mystmaiden,

In my experience, upgrading works fairly well.

Personally, I always do a clean install of the new Ubuntu every 6 months. I take careful note of the packages I install, and any settings I change, so I can easily make my new installation have all the same features as the previous one.

But in saying that, I do maintain 6+ Ubuntu machines for friends and family, and I've done upgrades on a regular basis. I've only ever had it go bad once.

So I suppose my advice is - (1) do a backup first, (2) upgrade away, and (3) if you do the upgrade, I'd still suggest a clean install every 2-3 upgrades, just to keep things tidy!

Hope this helps :)

Callan

---

### Post by mystmaiden on 2009-08-09
Thanks, Callan. I could probably stand to do a clean install, leaving a separate partion for / and adding a partition for data but after my dual boot fiasco, upgrading is looking pretty good. One thing that leaves me cold about a clean install is Poser, its a beast getting it all installed and all the various junk back into it. If I had been really smart I'd have put it on its own separate hard drive.

myst

 Do you keep track of changes and added packages as you go or just note them right before the clean install?

---

### Post by LewRockwell on 2009-08-09
had upgrades fail in the past so we just install fresh after appropriate back-ups/clones/etc

also, REGARDLESS of whether you upgrade or fresh-install...

you should try out the LiveCD of the version you want to move to...FIRST...before things don't go as planned and you are then required to revert back to what you had before...

hey, it's your time and you can NEVER get it back...

.

---

### Post by Christmas on 2009-08-09
My upgrading with Ubuntu updating usually broke things. You can however upgrade from Hardy to Intrepid and then to Jaunty, either the graphical way or by editing /etc/apt/sources.list, replacing **hardy** with **intrepid** and then performing **sudo apt-get update && sudo apt-get dist-upgrade**. Then repeat this step for Jaunty. However, if you don't care much about configuration you have in Hardy and you can do it all over again on a clean system, I would advise to make a clean install, but just make sure to back-up stuff you need before partitioning and formatting.

---

### Post by XCan on 2009-08-09
On my three machines (starting from 8.04) I've always went with upgrade. They are now all running 9.04, and haven't had any issue so far. Of course, I am not much of a ninjahacking guy, so my installations are all pretty standard with almost no installed applications from outside the repos or tweaked configuration files, which significantly lowers the breaking probability when upgrading.

---

### Post by LewRockwell on 2009-08-09
> **XCan said:**
> On my three machines (starting from 8.04) I've always went with upgrade. They are now all running 9.04, and haven't had any issue so far. Of course, I am not much of a ninjahacking guy, so my installations are all pretty standard with almost no installed applications from outside the repos or tweaked configuration files, which significantly lowers the breaking probability when upgrading.

we're not sure where "which significantly lowers the breaking probability when upgrading" comes from

EVERY breakage/problem we have ever experienced was on a generic/default installation with absolutely nothing out of the ordinary

we are glad that some have upgraded uneventfully, but will continue to highly recommend against it

.

---

### Post by thiebaude on 2009-08-09
Whenever i upgrade from one version to another i just did:

update-manager -d

---

### Post by zvacet on 2009-08-09
If you don´t have separate home make one following [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.If you want to upgrade do it with alternate CD.That way you will always have CD in case you need it or if you want to give it to somebody.In your case I will do fresh install with alternate CD,because it is less time consuming then upgrading two versions.

---

### Post by XCan on 2009-08-09
> **LewRockwell said:**
> we're not sure where "which significantly lowers the breaking probability when upgrading" comes from

EVERY breakage/problem we have ever experienced was on a generic/default installation with absolutely nothing out of the ordinary

we are glad that some have upgraded uneventfully, but will continue to highly recommend against it

.

That's unfortunate, downright sad tbh. Not even Windows needs to be reinstalled that often (slowdown issues, not infection issues). :(

---

### Post by mystmaiden on 2009-08-09
Thanks everyone for the input, I really appreciate it. I did test out the live version of Jaunty, and it seemed to work fine. I had sound and video. Right now I've hit some snags with backup, but that is definitely the next step. 

Lew wrote:

> we're not sure where "which significantly lowers the breaking probability when upgrading" comes from

EVERY breakage/problem we have ever experienced was on a generic/default installation with absolutely nothing out of the ordinary

we are glad that some have upgraded uneventfully, but will continue to highly recommend against it 

silly question here, who is 'we'? 

myst

---

### Post by callan79 on 2009-08-10
> **mystmaiden said:**
> Do you keep track of changes and added packages as you go or just note them right before the clean install?


Hi mystmaiden,

Sorry for the late response ... had a busy day!

To answer your question, I have just kept a list of the "essentials" - you know, all the stuff that MUST be installed to keep me happy. Then if I forget anything I can just install it later.

I keep all this data in a text file. This way I can just "sudo apt-get install (paste)" and all my essentials just slide on with ease.

Here's what I install as my essentials, you might find it useless, but it would also be interesting to see how other people do it ?

```

ESSENTIALS
sudo apt-get install nautilus-image-converter libjpeg-progs gqview vlc exiftran jhead hugin renameutils conduit multisync libmultisync-plugin-all elisa easytag ubuntu-restricted-extras helix-player mozilla-helix-player deluge-torrent gftp gnome-rdp grsync cheese gthumb screenlets nload vnstat ssh

FONTS
sudo apt-get install ttf-dustin ttf-georgewilliams ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon ttf-gentium ttf-sjfonts

```



Also,  I thought I'd post here about my process for installing a new version of Ubuntu.

I have four partitions ...

[LIST]
[*]swap
[*]/ (ext3)
[*]home (ext3)
[*]data (ext3)
[/LIST]

So what I want to do is preserve my old home folder just in case I forgot to back up something (eg bookmarks, etc). My home folder is called 'callan'

So I mount my /home partition using the live CD, and rename 'callan' to 'callan-old'

Then I install the new Ubuntu, choosing NOT to format the home partition. Ubuntu kindly makes a new 'callan' folder for me, and then I keep 'callan-old' just in case I need something.

Again, this might all be useless info, but I'm still curious as to what others do?

Mystmaiden hopefully your new installation is working well by the time you read this :)

Cheers
CD

---

### Post by 3rdalbum on 2009-08-10
Upgrading works well in my experience. The official way to upgrade is to go to System > Administration > Software Sources and click the Updates tab, and then tell it to show all new distribution releases (not just LTS releases).

Run the Update Manager and check for new updates. If you're not told of a new distribution release, try updating your Hardy system first, and then wait a couple of minutes.

That's the official, and most intelligent*, way to upgrade your system.

*By "intelligent" I mean that the Update Manager program has some extra workarounds programmed into it for various circumstances.

---

### Post by wizard10000 on 2009-08-10
JMO but this is how I upgrade:

1.  Copy the contents of /home and /etc to an external drive.

2.  I get a list of all my installed packages like this -

```
dpkg --get-selections > package_list.txt
```

2a.  If you're not changing architecture you can also back up /var/cache/apt/archives so you don't have to download the packages over the internet.  If you're changing from 32-bit to 64-bit architecture or vice versa you can skip this step.

3.  Clean install the new version of Linux.  This time put /home on its own partition so you can do the next upgrade without blowing away your /home partition.

4.  You can restore your home directory but don't restore /etc - just keep it around for awhile so you can replace any configuration files for packages you install.

5a.  Get ready to reinstall your packages.  If you're not changing architectures then just copy your backup of /var/cache/apt/archives and run

```
sudo apt-get update
```

5b.  Reset your selections and reinstall packages like this

```
dpkg --set-selections < package_list.txt

sudo apt-get dselect-upgrade
```

All done  ;)

---

### Post by theozzlives on 2009-08-10
> **XCan said:**
> That's unfortunate, downright sad tbh. Not even Windows needs to be reinstalled that often (slowdown issues, not infection issues). :(

Actually it's always better to do a fresh install with Windows. The downside is you can't put "Documents and Settings" on a separate partition like you can with /home.

---

### Post by wizard10000 on 2009-08-10
> **theozzlives said:**
> Actually it's always better to do a fresh install with Windows. The downside is you can't put "Documents and Settings" on a separate partition like you can with /home.

You can, but you have to create an unattended install script.  Been there, did that on an enterprise level - but we learned that a heck of a lot of Windows *applications* don't like the profile on another partition - but the OS doesn't mind it at all.  

In the end we rolled off the idea because a lot of application developers hardcode the location of Documents and Settings in their application.

---

### Post by theozzlives on 2009-08-10
> **wizard10000 said:**
> You can, but you have to create an unattended install script.  Been there, did that on an enterprise level - but we learned that a heck of a lot of Windows *applications* don't like the profile on another partition - but the OS doesn't mind it at all.  

In the end we rolled off the idea because a lot of application developers hardcode the location of Documents and Settings in their application.

One more good thing about Linux using mount points instead of drive letters. If Microsoft wants to survive they need to start from scratch, instead of "feeding oats to a dead horse".

---

### Post by wizard10000 on 2009-08-10
> **theozzlives said:**
> One more good thing about Linux using mount points instead of drive letters. If Microsoft wants to survive they need to start from scratch, instead of "feeding oats to a dead horse".

Yeah, but we can't blame MS if outside application developers can't follow simple programming concepts  :D

I used to be a Microsoft MVP - beta tested every desktop OS between Windows 95 and Windows XP and have some dated but official certifications after my name.  Used to be solidly in their camp and just dabbled in Linux - when Vista and Office 2007 came out I decided I wasn't giving them any more money and switched to Linux full-time  :)

Windows 2000 was clean code - which is a pretty good trick concering the amount of legacy hardware and software they had to support.  If MS took the same tack as Apple and just told everybody to buy new software when they upgraded their OS we wouldn't have to deal with this pesky legacy support thing  :)

---

### Post by saivin on 2009-08-10
Thank you wizard for the above post.  

Please let me know if I understood correctly.
 1. We get information regarding all the packages we have installed.
 2. We update our sources.list to have information regarding latest packages available in the repo.
 3. We tell dpkg to upgrade only the packages that are in packages.list to the latest version available.

Have few  doubts though.
1. I have few entries with gstreamer with 'deselct'. How does --get-selection determine that these packages need to be removed?

2. Can you please elaborate: > If you're not changing architecture you can also back up /var/cache/apt/archives so you don't have to download the packages over the internet. If you're changing from 32-bit to 64-bit architecture or vice versa you can skip this step.

---

### Post by wizard10000 on 2009-08-10
> **saivin said:**
> Thank you wizard for the above post.  

Please let me know if I understood correctly.
 1. We get information regarding all the packages we have installed.
 2. We update our sources.list to have information regarding latest packages available in the repo.
 3. We tell dpkg to upgrade only the packages that are in packages.list to the latest version available.

Have few  doubts though.
1. I have few entries with gstreamer with 'deselct'. How does --get-selection determine that these packages need to be removed?

2. Can you please elaborate:

Sure  ;)

1.  Yup.  That's how it works.

2.  I was talking about a clean install, which would have the proper repos configured automatically.

3.  Also yes, because --get-selection only lists package names, not version numbers.

also -

--get-selection lists all selected packages, not just packages that are selected to install.  If a package is selected to be removed it'd still be removed.

Best thing I can suggest is to run --get-selection and dump it to a text file so you can browse the file.  You should see packages marked for removal in there if you have them already selected.

---

### Post by saivin on 2009-08-10
What about backing up /var/cache/apt/archives/ ? We have to download if we have latest versions right?

---

### Post by wizard10000 on 2009-08-10
> **saivin said:**
> What about backing up /var/cache/apt/archives/ ? We have to download if we have latest versions right?

Depends.  The latest version for Intrepid may or may not be the latest version for Jaunty  ;-)

If you put all that stuff back in /var/cache/apt/archives and run apt-get update apt will update its own database and if what's available in the repos is newer it'll grab the newer version.

---

### Post by mystmaiden on 2009-08-15
This has been a great thread for me, I learned a lot from it. I appreciate all the input! In the end, I updated to 8.10 and everything worked well but desktop drapes, it continued to give me errors. But in the end I managed to fool around and break 8.10 by trying to customize a system sound (it made my computer stop shutting down). That one I did not find a work around for, so I did a clean install of Jaunty late last night. As Callan suggested, I'll be keeping track this time of what changes I make along the way to make the next go around easier. So far Jaunty is working well except that it doesn't want to start drapes on start up either, but no error message now - I just have to remember to launch it. I don't have a video card yet so no desktop effects which seem to be the issue with jaunty freezing.

mystmaiden

---

