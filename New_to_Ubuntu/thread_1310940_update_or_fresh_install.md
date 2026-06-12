---
title: "update or fresh install?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by levis lover on 2009-11-02
i have a sony vaio with ubuntu 9.04 installed on my system..
i want to check out the new 9.10
shall i upgrade to the new OS or shall i do a fresh install?
Also what is the difference between simple ubuntu and the netbook  remix..
which would be better for the laptop and how?

---

### Post by Zzl1xndd on 2009-11-02
Genereally speaking I prefer a fresh install, as it cleans everything up. However upgrades have worked well for me in the past. 

The Netbooks Remix is really aimed at machines with 10 inch screens or smaller. Probably wouldn't recomended if you have a full sized laptop.

---

### Post by feb3 on 2009-11-02
Having had problems with the upgrade (as outlined in the forum by many others) I have gone back to Jaunty.
My advice would be to try a live CD. At least you would then be able to use it to do a clean install if the upgrade failed.

---

### Post by etali on 2009-11-02
One of the biggest features of Karmic is faster boot times.  If you do an update, you'll also need to manually update GRUB to take advantage of those faster boot times.

If you do a clean install, it will update GRUB for you.  I'm lazy, and don't have much to back up, so that's the route I take :)

I second the suggestion of testing with a live CD to make sure all your hardware is supported first.

---

### Post by JOHNNYG713 on 2009-11-02
Hi First I would download and burn a 9.10 live ,install CD and test everything with the live CD, If everything works out or you know how to overcome those that don't and you are comfortable with 9.10, (As some things have changed,maybe do some research on the new changes so you know what to expect.)Then I would back up my home folder and other important items and do a fresh install ,That way you have all the new goodies, but you still run the risk of problems (as with any "new" install), OR you could wait for Ultimate Edition 2.4 (Thats what I would do !) any way good luck hope all goes well for you ! :D

---

### Post by sdpiowa on 2009-11-02
It's a good idea to test 9.10 with a Live CD.  If everything works, I recommend backing up your files and installing from scratch.

I've only had one instance where the upgrade manager failed, but I still recommend a clean install most of the time.

---

### Post by zkriesse on 2009-11-02
Test the new version via a Live CD on your pc. If it works ok then do a full install.

---

### Post by MelDJ on 2009-11-02
google your problem. i am sure you will find other people comments on it and what they did.

---

### Post by Xomm on 2009-11-02
I'd say trial out the LiveCD, compatibility check, etc. 

Fresh install.

and @JOHNNYG713's post:

Don't try minor spin-offs until you try the original distro.

---

### Post by bashphoenux on 2009-11-02
upgrade saves time !!!  no need to back up your home and stuff !!  but as others stated if you have time fresh install is better :)

---

### Post by admiralspark on 2009-11-02
Hey,
if you have 9.04 installed in ubuntu through WUBI, I suggest you completely uninstall it and then install 9.10. I upgraded from 9.04 on the wubi install and basically wrecked the shutdown procedure, as has been reported in several places on the forums. 9.10 installed to the HD is much faster startup/shutdown.
The Netbook remix is definitely not for fullsize laptops, trust me. Ubuntu full runs much lighter than windows to begin with, so.....

---

### Post by danielsk on 2009-11-02
If I'm going for a fresh install, which folders should I avoid in order to loose my previous configurations?

I'm not sure how but I messed my sound quite a bit and I'd like to install over without keeping the previous configurations.

---

### Post by LewRockwell on 2009-11-02
[http://ubuntuforums.org/showthread.php?t=1308317](http://ubuntuforums.org/showthread.php?t=1308317)

.

---

### Post by Old *ix Geek on 2009-11-02
> **bashphoenux said:**
> upgrade saves time !!!  no need to back up your home and stuff !!If you've installed things on separate partitions, there's no need to back up your data when doing a fresh install.  In other words, when you're initially partitioning the hard drive, if you allocate space for /, and separate space for /home (and other partitions if you'd like), then install the OS on /, from that point on you can safely format the root partition without losing anything in /home. (This assumes that you're not saving data on /, of course.) That's what I do.

Note that I'm definitely NOT saying you shouldn't do backups! I'm not.  It's always, always a good idea to keep current backups. I'm referring only to the issue of doing a fresh install. You don't have to worry that you'll lose data *IF* you've used the partitioning scheme mentioned above.

---

### Post by H2SO_four on 2009-11-02
> **Old *ix Geek said:**
> If you've installed things on separate partitions, there's no need to back up your data when doing a fresh install.  In other words, when you're initially partitioning the hard drive, if you allocate space for /, and separate space for /home (and other partitions if you'd like), then install the OS on /, from that point on you can safely format the root partition without losing anything in /home. (This assumes that you're not saving data on /, of course.) That's what I do.

Note that I'm definitely NOT saying you shouldn't do backups! I'm not.  It's always, always a good idea to keep current backups. I'm referring only to the issue of doing a fresh install. You don't have to worry that you'll lose data *IF* you've used the partitioning scheme mentioned above.


This is the same method that I use.  Prep for an upgrade/re-install consists of moving whatever is saved on my desktop and inserting the live cd.  

I did an upgrade and also a full install and they both worked flawlessly.  No problems whatsoever.

---

### Post by bodhi.zazen on 2009-11-02
Update and if you have problems fresh install.

Back up your data first, separate partition or not you should always have a working backup =)

---

### Post by bubbles99 on 2009-11-02
I would test Ubuntu 9.10 on a LiveCD first, and if everything works do a fresh install **_AFTER_ BACKING UP YOUR FILES!!!** Also, you could use APTonCD to reinstall your packages without fuss. Just be aware that some of your packages may no longer be supported.

---

### Post by CAPLinux on 2009-11-02
I did a fresh install and WOW what a difference.  The PC is extreamly fast now.  Fresh installs are always a better option.

---

### Post by danastasio on 2009-11-02
i personally recommend using a liveCD to test the system and make sure there are no problems (i had sound issues). If you like the system (and remember, it's going to be slow as heck on a LiveCD) then i recommend a fresh install. It gives you a chance to flush out the file system, of say, files and folders from programs that you compiled but no longer use. And i personally have had issues with the update manager. I used it going from hardy to intrepid, but for everything else, it was a fresh install. Do you have your home folder on a seperate partition? If thats the case, i wouldnt worry about a fresh install at all.

---

### Post by gdonwallace on 2009-11-02
I would start by running the LiveCD and see how things work on your system.

As to the upgrade / fresh install question.  I have done both, though not by choice.  I did the upgrade on my desktop and have had no problems.  I had to do the fresh install on my laptop.  Had some really odd issues with my Master Boot Record and could not get any versions of Ubuntu to install and run, so it was not a problem with Ubuntu.  I did a low-level format to erase the MBR and then completely installed 9.10, again no problems from this install.  

It all comes down to choice.  If you have data that you can't / won't backup and want the latest, then do the upgrade.  If you don't have anything on your system that you don't mind loosing, then do the clean install.

---

### Post by jaycee23 on 2009-11-02
> **JOHNNYG713 said:**
> Hi First I would download and burn a 9.10 live ,install CD and test everything with the live CD, If everything works out or you know how to overcome those that don't and you are comfortable with 9.10, (As some things have changed,maybe do some research on the new changes so you know what to expect.)Then I would back up my home folder and other important items and do a fresh install ,That way you have all the new goodies, but you still run the risk of problems (as with any "new" install), OR you could wait for Ultimate Edition 2.4 (Thats what I would do !) any way good luck hope all goes well for you ! :D

I would agree with JonnyG - exactly what I did and very few issues since doing a fresh install. Did have the advantage of /home being on a separate partition which made things a lot easier.

Hope you enjoy the Koala!

---

### Post by levis lover on 2009-11-06
now here's another query..
about softwares such as VLC and other codecs..
if i do a fresh install i will have to install them from scratch again..
will copy pasting those softwares directly from 9.04 into 9.10 work?

---

### Post by SunnyRabbiera on 2009-11-06
Karmic seems to perform better with fresh install

---

### Post by mikechant on 2009-11-06
> now here's another query..
about softwares such as VLC and other codecs..
if i do a fresh install i will have to install them from scratch again..
will copy pasting those softwares directly from 9.04 into 9.10 work?

Yes, you should reinstall these.
It's almost never a good idea to copy stuff like this across. Many software packages (including codec packages etc.) will have new versions, and the old versions may not work correctly on the new Ubuntu version.

---

### Post by whoop on 2009-11-06
> **bodhi.zazen said:**
> Update and if you have problems fresh install.

Back up your data first, separate partition or not you should always have a working backup =)

I agree with this, although with a slight edit:

*Update and if you have problems*, try to fix them and if you can't,* fresh install*

---

