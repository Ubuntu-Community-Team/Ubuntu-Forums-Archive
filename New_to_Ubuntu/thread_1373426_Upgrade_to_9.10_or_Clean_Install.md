---
title: "Upgrade to 9.10 or Clean Install?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by JBA2337 on 2010-01-05
I am now running Ubuntu 9.04. If I install the new version 9.10, would it be better to format my Ubuntu partition and do a clean install, or is it better to do an upgrade? THe Update Manager offers to upgrade my 9.04 installation to 9.10.

I don't want to have to re-install all of the software packages  that I have already installed, so the upgrade looks like it would be the easiest way to go, but is that a good idea?

I know that with Windows, it is usually best to do a clean install, so you won't end up with a lot of old code left over. 

What is the recommendation for upgrading Ubuntu? Clean install or upgrade?

JBA2337

---

### Post by LuisGMarine on 2010-01-05
+1 for clean install

Too many people are having issues with the upgrade from 9.04 to 9.10 through the update manager.  Unfortunately I don't think it works out like the developers intended it to.

---

### Post by Joeb454 on 2010-01-05
I generally do a clean install anyway :) Just because I can.

Though I tend to keep the same /home partition, so it's been a while since I've done a **true** clean install.

---

### Post by =not4prophet= on 2010-01-05
Having done both, I would recommend doing a clean install.

---

### Post by bodhi.zazen on 2010-01-05
UPGRADE FTW !!!!

If it breaks fix it.

If you can not fix it, clean install.

Currently have an 8.04 -> 8.10 -> 9.04 -> 9.10 laptop, occasional problems, nothing too bad.

The upgrade process is much better now, IMO, then in the past.

---

### Post by howefield on 2010-01-05
The polls conducted shortly after 9.10 was released seemed to show the better chance of success through a clean install.

In terms of the installed packages, have a read here, might make the install slightly easier.

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

---

### Post by 00ber n00b on 2010-01-05
> **LuisGMarine said:**
> +1 for clean install

Too many people are having issues with the upgrade from 9.04 to 9.10 through the update manager.  Unfortunately I don't think it works out like the developers intended it to.

Oorah! 8th Marines (former)

I would back up all files, try a clean install.  If that doesn't go well, then I would try clean.

---

### Post by howefield on 2010-01-05
> **00ber n00b said:**
> I would back up all files, try a clean install.  If that doesn't go well, then I would try clean.

So, that would be a clean install then ?


:lolflag:

---

### Post by colin.p on 2010-01-05
Most recommend a clean install. However, I have upgraded since intrepid and have had absolutely no issues, at least none that come to mind. I do wait a month or so after the release date to update.
I will, however, do a clean install of lucid again a month or so after it comes out, then do updates after that all the way to the next long term release, or until something breaks. 

Colin

---

### Post by running_rabbit07 on 2010-01-05
I did the dirty install from 9.04 to 9.10 and had zero problems. I have had a few hexed clean installs with Karmic. But I should say that Karma owes me much strife.

---

### Post by Linux000 on 2010-01-05
If you have an ext3 partition now, clean install else, try upgrading.

---

### Post by chaanakya_chiraag on 2010-01-05
Trust me...clean install is better.  To make installing less of a hassle, do the following:
1) Create a separate /home partition.  When the installer starts up the disk partitioner, click manual.  Then, on the next screen, create one partition for /, one partition for /home, and one partition for swap.
2) Run the following command once in a while:
```
sudo dpkg --get-selections > installed-software
```
3) Run this one also once in a while (from your home directory):
```
sudo cp /etc/apt/sources.list .
```
The above command will create two files: one called installed-software that contains a list of all installed software and another called sources.list that should have a lock emblem on it and contains a list of all your software sources.  To automagically reinstall all of the sofware you had installed before you clean-installed, simply type ```
sudo dpkg --set-selections < installed-software
```  To restore your sources, simply double-click on the sources.list file and Ubuntu will do the rest!
- Chiraag

---

### Post by kansasnoob on 2010-01-05
I'm adventurous so I prepare for a clean install just in case things go horribly wrong, then I upgrade. If the upgrade stinks then I can do a clean install.

---

### Post by gshockxc on 2010-01-05
I'm confused.  (NO surprise there - N00B)

I was running Kubuntu 9.04.  I got the little pop-up that 9.10 was available, and I finally got around to installing it this morning.  I came back after all the packages had downloaded, and restarted my machine.  Now I've got a stinking Gnome desktop with no KDE.  What the heck?  

Did I do something wrong?  Did I pick an incorrect option somewhere, or miss a check box?  Don't get me wrong, Gnome is fine, it's just not what I wanted.  I really like the KDE interface, and I have a 64 bit system.  So what are my options?  Clean install of 9.10?

How do I back up all my files?  Do I transfer them all to my external hard disk, or partition the drive or something?  I saw chaanakya_chiraag's post, and I was thinking of doing that before I burn the .iso and try a clean install.

I'm such a dumba$$ ](*,) ](*,) (one more time for good measure...](*,)

---

### Post by Linux000 on 2010-01-05
Hmm... first backup your files, there are a lot of backup programs in the software center. 

Then (if you can spare 2GB of disk space) go into terminal and type ```
sudo apt-get install kubuntu-desktop
``` that will install kubuntu, just select it at the bottom bar when you log-in. If you can't spare 2 GB, a clean install is your best option.

---

### Post by running_rabbit07 on 2010-01-05
:)That is because they discontinued Kubuntu.:)


Seriously, that sucks. I never imagined that could happen. Back up you personal files to an external drive and reinstall. Make the /home in the new install, for best results.

---

### Post by gshockxc on 2010-01-05
... actually, it didn't happen.  It's just that I'm more a dumba$$ than your average ..., er, well, dumba$$, I guess.


I was having some issues with my CD drives.  For some reason, they both locked up when I tried to burn the .iso image, which was on the Gnome desktop.  So I figured I'd restart.  Turns out, there's a little button on the lower left of the Kubuntu login screen.  You can select the type of desktop environment.  I clicked on KDE, and everything I had before came right back to where it was.  All my desktop frillies are back where they belong.  So what was broke ain't broke ... yet.  Let me play with it a while, and I'll be sure to screw up something.

---

### Post by kansasnoob on 2010-01-05
If you have mixed Gnome and KDE and want pure KDE this may interest you:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by gshockxc on 2010-01-05
Yeah, I'll definitely hit that up later.  Not getting down on Gnome, I just really like the look of KDE.  Thank you for that. 

What I'd really like to get back are the tabs that show which programs I have running.  The panel used to have these, and I goofed up something and I can't get them back.  The only way to find what programs I have running (if I've minimized things) is Alt+Tab, or to find the "Show Hidden" corners of the desktop.  For me, when I move my mouse to the far right really quickly, it shows me all the programs I have open.  Similar to what the Mac's do, as I've recently learned.

---

### Post by ubudog on 2010-01-05
Would go with clean install.  Just copy your home directory to a cd or usb flash drive and make a clean install.  Have had some problems with the upgrades.

---

### Post by WA4MOE on 2010-01-06
Well, I just did an upgrade install and all went just splendid -no issues found yet (2 days)

---

### Post by slakkie on 2010-01-06
> **Joeb454 said:**
> I generally do a clean install anyway :) Just because I can.

Though I tend to keep the same /home partition, so it's been a while since I've done a **true** clean install.

That is a **true** clean install dude.

Ps. [http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/)

---

### Post by milinda_pathirage on 2010-01-06
+1 for clean install. Me and some my friends experienced some issues after upgrade. I managed to fix it to some extent, but my friend did a clean install.

---

### Post by chaanakya_chiraag on 2010-01-06
The command should be
```
sudo cp /etc/apt/sources.list .
```
You have to remember the "." at the end :)

---

