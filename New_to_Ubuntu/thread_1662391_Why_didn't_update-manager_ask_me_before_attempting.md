---
title: "Why didn't update-manager ask me before attempting to install 10.10?"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by asuastrophysics on 2011-01-08
After finally running update-manager after letting it collect updates for a few weeks, I get a message at the end saying "Not all updates could be installed. Hit "Partial update" to continue". I hit partial update and....

GAHHH!!! Why doesn't the update manager tell you when it's trying to upgrade to a new distribution?? I don't ever want to update my distribution ever again. No 10.10. No more bugs undoing perfectly working software ("regressions"). I can't take it anymore. Every time I choose to do an upgrade, it always ends up with me losing all of my data and having to completely reformat the drive and start from scratch.  I "force quitted" the update-manager as it was about to do the first step in the "upgrade".

Is my installation already corrupt? How can I set update manager to not trick me into updating to a new distribution? I thought That you had to hit the "upgrade" button on the update manager to do that. Who and why has it been changed to perform it otherwise? Thanks. I just want my computer to work. If that means staying with LTS for as long as humanly possible, then so be it. Any suggestions?

---

### Post by asuastrophysics on 2011-01-08
Yup, it took 2 seconds for Ubuntu to completely destroy my machine. I just now tried to install some packages for ubuntu to communicate with my iphone. This is what I got:
```
jake@jake-desktop:~$ sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libimobiledevice-utils libimobiledevice1 python-imobiledevice libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgvfscommon0 is already the newest version.
libimobiledevice-utils is already the newest version.
libimobiledevice1 is already the newest version.
libimobiledevice1 set to manually installed.
libusb-1.0-0 is already the newest version.
libusb-1.0-0 set to manually installed.
[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.[/B]
[B]The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gvfs: Conflicts: libgvfscommon0 but 1.6.1-0ubuntu1build1 is to be installed
E: Broken packages
jake@jake-desktop:~$ [/B]

```

Every time I install any packages from terminal now, update manager pops up a window asking to do a "partial upgrade". If I hit "partial upgrade, it asks me to start the complete upgrade. Why is it asking me to do a "partial", when all it really wants to do is do the full one?
How do I fix this? I'm getting desperate! Help if you can please!!!

---

### Post by anjilslaire on 2011-01-08
According to [this]("http://www.uluga.ubuntuforums.org/showpost.php?p=9247783&postcount=5") a Partial Upgrade means you have repository problems. Check your repository ist & set it back to just the previous OS's repositories, nothing extra. Then do an apt-get update then apt-get upgrade to install just the regular updates.
 
Otherwise, set Update Manager to never provide distro updates if desired: 
Update Manager>Settings>Updates>Release Upgrade>Never

Also, stick nto installing /home on it's own partition so you can wipe or reinstall the OS at will and never lose your data & settings.

---

### Post by Zill on 2011-01-08
> **anjilslaire said:**
> ...Otherwise, set Update Manager to never provide distro updates if desired: 
Update Manager>Settings>Updates>Release Upgrade>Never

Also, stick to installing /home on it's own partition so you can wipe or reinstall the OS at will and never lose your data & settings.
+1
and, of course, *always* keep regular backups of your data!

---

### Post by asuastrophysics on 2011-01-09
I did everything mentioned, as far as "deleting" newer repositories from the sources list and running apt-get update and upgrade. However, I didn't find any 10.10 sources in my list. When I ran "apt-get upgrade", Ubuntu held back "gvfs" from being updated. 

Now, if I refuse to hit "partial upgrade" in the update-manager dialogue box, the entire update-manager list of things needing updates completely grays out, so I can't update anything. :( Any other suggestions? 

In my /etc/apt/ folder, I have two files. One says "sources.list", and the other says "sources.list.distUpgrade". Should I just delete the *.distUpgrade file?

Also, should I file a bug report against update-manager? It really shouldn't try to update the distribution unless you hit the "upgrade" button on the top of the window. Is this a bug?

Contents of my sources.list file:
> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by colin.p on 2011-01-09
I got that message a couple of times, but just let it update. The first time, I was surprised and thought it was asking to upgrade to 10.10, (I did have it marked in "update mgr" to upgrade to a newer release when available, but usually it asked specifically to upgrade. I wasn't planning on upgrading but thought oh well if it's going to...), but it only updated the listed package updates no release upgrade. The next time, I looked carefully and still it didn't upgrade to 10.10, I am still running lucid. I then went back into update mgr and made sure that the "upgrade to a new release" button was unchecked.
I think that the message could be a bit clearer, but so far, I don't think it will upgrade unless you specifically tell it to upgrade to a new "normal" release, just upgrade to a new LTS version. It will still do updates, not upgrade to a new release.

---

### Post by Zill on 2011-01-09
> **asuastrophysics said:**
> I did everything mentioned, as far as "deleting" newer repositories from the sources list and running apt-get update and upgrade. However, I didn't find any 10.10 sources in my list...
So *which* repos did you actually delete?  Your current list now only shows 9.10 Karmic Koala sources.  On this basis, I am puzzled as to *why* your system apparently tried to upgrade to 10.10 Maverick.  9.10 Karmic is a "normal" release and, as such, should only directly upgrade to the next release, i.e 10.04 Lucid.  Which release do you actually want to run?  Please also advise the output of the following command, which will show the current installed release:
```
cat /etc/lsb-release
```
In any event, upgrades to the next release should only happen with your explicit permission *and* in accordance with your preferences set as described by anjilslaire in [post #3]("http://ubuntuforums.org/showpost.php?p=10330875&postcount=3") above.
> **asuastrophysics said:**
> In my /etc/apt/ folder, I have two files. One says "sources.list", and the other says "sources.list.distUpgrade". Should I just delete the *.distUpgrade file?...
As I am unsure exactly what has happened here I cannot give definitive advice.  AIUI, the "sources.list.distUpgrade file is apparently a backup file of the "old" sources list created during the process of upgrading to the next release.  Personally, I would try renaming "sources.list.distUpgrade" so that it is temporarily ignored eg.
```
sudo mv sources.list.distUpgrade sources.list.distUpgrade_test
```
I would then try to update/upgrade in the usual way and see what happens.  Hopefully, it may bring your system back to a stable state but if not you should be able to rename the file back again if necessary.  Note that this will be with 9.10 Karmic as this is the release defined in your current sources list.  Do this at your own risk though unless someone else can confirm it is a good move ;-)
> **asuastrophysics said:**
> Also, should I file a bug report against update-manager? It really shouldn't try to update the distribution unless you hit the "upgrade" button on the top of the window. Is this a bug?
As already suggested, this really should not happen with the default settings.  Unless you are *absolutely* sure you have not changed the defaults then I suggest this is not really a bug, just good old-fashioned finger trouble :-)

---

### Post by asuastrophysics on 2011-01-10
> **Zill said:**
> So *which* repos did you actually delete?  Your current list now only shows 9.10 Karmic Koala sources.  On this basis, I am puzzled as to *why* your system apparently tried to upgrade to 10.10 Maverick.  9.10 Karmic is a "normal" release and, as such, should only directly upgrade to the next release, i.e 10.04 Lucid.  Which release do you actually want to run?  Please also advise the output of the following command, which will show the current installed release:
```
cat /etc/lsb-release
```


Thanks for your input buddy! (And everyone else as well!) Here is what I have so far...

```
jake@jake-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

```
Very, very weird. I never touched the file, or changed anything about it. :???:

> **Zill said:**
> As already suggested, this really should not happen with the default settings. Unless you are absolutely sure you have not changed the defaults then I suggest this is not really a bug, just good old-fashioned finger trouble
To the best of my knowledge, I have never changed any settings at all in the "software sources" window, since installing ubuntu. Below are the settings I have checked under the "updates" tab in the "software sources" window:

Important Security Updates (lucid-security) CHECK
Recommended updates (lucid-updates) CHECK
Check for updates: "Daily"
Only notify about available updates CHECK
Show new distribution releases "Long-term support releases only"

(any settings not specifically mentioned should be assumed "unchecked".

---

### Post by mastablasta on 2011-01-10
if you added a PPA or tried to install some other software (outside of resources) or tried to go with a newer version of software you will get a partial upgrade because newer software version needs libraries found in the ubuntu system.
 
for example it is possible to have newer version of Empathy but if you add the PPA or try to installit through other means it will perform sort of partial upgrade.

---

### Post by colin.p on 2011-01-10
> **mastablasta said:**
> if you added a PPA or tried to install some other software (outside of resources) or tried to go with a newer version of software you will get a partial upgrade because newer software version needs libraries found in the ubuntu system.
 
for example it is possible to have newer version of Empathy but if you add the PPA or try to installit through other means it will perform sort of partial upgrade.

Thanks, that explains it very well. Makes sense actually.

---

### Post by Zill on 2011-01-10
asuastrophysics:  I don't *fully* understand what is going on here as the output from /etc/lsb-release shows that you are running 10.04 Lucid although your sources list shows 9.10 Karmic :confused:  However, mastablasta has given a good explanation of *how* this is likely to have happened.

Unfortunately, you now seem to be in "dependency hell" and, unless you wish to spend many hours trying to rebuild the system to a stable state, I suggest your best action is to re-install.

You did not make it clear which release you actually want to run but I suggest you decide on 10.04 (LTS) or 10.10 (normal) and then reformat and install from scratch.  Prior to this you will need to ensure that your data is fully backed up elsewhere.  If you do not already have current backups then you should be able to use the live CD to copy data from your HDD.

During the new installation you will be able to specify a separate /home partition, which will ensure that you can retain your data following any future upgrades or OS installations.

A final word of advice is to be *very* wary of installing software that is not intended for your Ubuntu release, particularly if it installs additional dependencies, as this is *probably* the cause of your current woes!

Good luck.

---

### Post by Paqman on 2011-01-10
As a general rule, never do a "partial upgrade" if it's offered. It's a recipe for trouble.

---

### Post by asuastrophysics on 2011-01-11
> **Zill said:**
> asuastrophysics: Unfortunately, you now seem to be in "dependency hell" and, unless you wish to spend many hours trying to rebuild the system to a stable state, I suggest your best action is to re-install.

You did not make it clear which release you actually want to run but I suggest you decide on 10.04 (LTS) or 10.10 (normal) and then reformat and install from scratch.

Oh, no no no no NO! Please say it isn't so! You mean to tell me that all it takes to brick an Ubuntu computer is to install a piece of software with a newer version than what the repositories have listed???

Why is this fact not listed in the "When you install linux, be ready for these changes" page? (Whatever it's called. Transferring to Ubuntu, whatever.) Even though I have been using Ubuntu for 3 years, nobody in any thread has ever cast light on this issue.

This installation is only 6 months old. I have never been able to keep an installation of Ubuntu running for more than that without the OS completely committing suicide. 

Why is this allowed to happen? Why aren't more people forewarned about this? Why did the Update Manager allow me to install a newer version of software without updating repositories first? Furthermore, how is any of this evidence of a "stable" operating system? (Before anyone says "It's because you ALLOWED ubuntu to do it, let me ask you this: What software programmer at Canonical decided it was a good idea to allow the end user to completely destroy the OS by simply installing a newer piece of software? 

I might as well have just typed sudo rm -r / and just have gotten rid of everything. 

If this bricks my OS, I will back up all my data, reformat my HDD, install Windows 7, and never use linux again. That is the final nail in the coffin. I knew something was horribly wrong when I saw this. I didn't realize that things were this bad though.

> **Paqman said:**
> As a general rule, never do a "partial upgrade" if it's offered. It's a recipe for trouble.

If it's a recipe for trouble, then **why** is it offered? I'm filing a bug report. Furthermore, I will kindly invite the creators of this monstrous piece of software to come to my house, back up everything, do a complete reinstall, and re-install all the programs I now have that will be lost. I don't care that the software is free. If you were to multiply all the hair-pulling hours I've spent trying to "fix" Ubuntu once it dies, it would probably escalate into the thousands.

> **Zill said:**
> asuastrophysics:A final word of advice is to be very wary of installing software that is not intended for your Ubuntu release, particularly if it installs additional dependencies, as this is probably the cause of your current woes!

So what you're saying here is, don't install any software not specifically designed for Ubuntu 10.04, and don't install any .deb files, as they install their own dependencies. Are those the steps I need to take to insure this doesn't happen again?

---

### Post by wilee-nilee on 2011-01-11
I think we are all sorry to see any other user have problems, but I would be hard to convince this wasn't a user error. You can run whatever OS you want, threatening to go back to W7 will get you little sympathy.

---

### Post by asuastrophysics on 2011-01-11
I didn't say the things I said to gain sympathy or win favors. I appreciate the community's attempt at fixing my issue here, I really do. I say the things that I say not to "attack" or "offend" anyone, but only because these things need to be said, because nobody else is saying these things. I just want my computer to work longer than 6 months. If that means installing W7, then so be it. I'm not "threatening" to install W7. I am going to install W7 if this stupid repository problem can't be resolved, and that's a guarantee. I've had to reformat and reinstall Ubuntu probably 20 different times since I started using it. Most of that was my own fault, but then there are times like this where I wasn't "dinking around" at all. Only using and installing software, and somehow that's enough to need a reformat.

I'm sure this is user-error, but on an operating system in which the user is given 100% free-reign to do whatever destructive decision he wants, and where users (like me) are completely uneducated and obviously from the thread have no clue how the OS works, destroying the OS is completely inevitable, especially when all it takes to brick Ubuntu is "installing a piece of software"

What I have inadvertently installed to cause this mayhem is the Linux-equivalent of a virus. Linux does get viruses, only they're not malicious code, they're normal programs screwed up by an installation method from hell. If Ubuntu wants to be stable, it needs to completely throw out apt-get, deb, and "dependencies". All dependencies seem to do is cause problems. Why can't the OS just have a normal installation method? One that doesn't install programs in thousands of different places all over the hard drive and cause things like this to happen?

---

### Post by Paqman on 2011-01-11
> **asuastrophysics said:**
> 
If it's a recipe for trouble, then **why** is it offered? I'm filing a bug report. Furthermore, I will kindly invite the creators of this monstrous piece of software to come to my house, back up everything, do a complete reinstall, and re-install all the programs I now have that will be lost. I don't care that the software is free. If you were to multiply all the hair-pulling hours I've spent trying to "fix" Ubuntu once it dies, it would probably escalate into the thousands.


I sympathise entirely. [Partial Upgrades are a perennial cause of b0rkage on the testing branch]("http://ubuntuforums.org/showthread.php?t=1641400"), due to the inherent instability of the repos therein, but they are very rare on stable systems. FWIW the "partial upgrade" is the system's attempt to make the best of a bad situation. In a way, it's trying to be too clever. It only ever occurs when the sources it draws its software from are in a broken state, and it's trying to go ahead and work around the problem. IMO, the default behaviour in that situation should be changed to no update instead of partial, with the option there to do a partial for the brave/foolhardy or well-informed testing users.

I suspect yours will not be the first bug raised about this behaviour, but i've not kept track on any discussion that's resulted.

---

### Post by asuastrophysics on 2011-01-11
Is there some sort of main system "log" that logs the name of the installed software, the day it was installed, etc??

I haven't compiled anything lately, so it shouldn't be too hard to trace the culprit, provided the system does log what is installed via *.deb files or the Software Center.

---

### Post by Paqman on 2011-01-11
> **asuastrophysics said:**
> Is there some sort of main system "log" that logs the name of the installed software, the day it was installed, etc??


Sure:
```
/var/log/apt/history.log
```

---

### Post by asuastrophysics on 2011-01-11
I fixed my computer. Guess what programs cuased complete system instability? The official, "stable" versions of Wine, the official version of "winetools", and all of the things that can be installed with winetools, and a program called "jokosher". I have no idea what program that is, but I removed it as well.

I then backed-up and completely deleted the apt/sources.list and restored it with a brand new list from a "sources generator" website for 10.04. I ran "apt-get update", then "partial upgrade", to remove wine again...apparently apt-get remove wine didn't actually remove it. It also removed the latest RC kernel, which it said was corrupt and was trash. Now everything's fine! No more messages asking for "partial upgrade". So I assume that the repository hell I was in is now fixed. :D

So the lesson here is, the officially-supported versions of Wine, Winetricks, and Jokosher are apparently completely evil, and installing them will result in serious OS problems, which apparently are the fault of the end-user.

---

### Post by Paqman on 2011-01-11
Jokosher is a recording studio type app, i'm a bit surprised to hear you had that installed without knowing about it.

I suspect your problem wasn't that the actual packages are buggy, since other people have them installed without issue, but that your package manager got itself tied up in knots. Which is unlikely to be your fault unless you were trying to get it to do something odd.

Glad you've fixed your machine! Nothing worse than a broken system.

---

### Post by asuastrophysics on 2011-01-11
Thanks for your  help!!!

---

### Post by Zill on 2011-01-11
> **asuastrophysics said:**
> Oh, no no no no NO! Please say it isn't so! You mean to tell me that all it takes to brick an Ubuntu computer is to install a piece of software with a newer version than what the repositories have listed???
...
Why is this allowed to happen? Why aren't more people forewarned about this?
...
So what you're saying here is, don't install any software not specifically designed for Ubuntu 10.04, and don't install any .deb files, as they install their own dependencies. Are those the steps I need to take to insure this doesn't happen again?
I feel your pain!  Unfortunately, if *you* deviate from a default installation then *you* are responsible for what you install.

Comprehensive information on Ubuntu is readily available, clearly identifying what is wise and what is not!

[InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware") for example:
> In addition to the official Ubuntu repositories, it is possible to use third party repositories. Be careful, though - some are not compatible with Ubuntu and using them may cause programs to stop working or may even cause serious damage to your installation.
and [Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu"):
> There are times when you might want to add non-Ubuntu repositories to your list of software sources. Make sure that all repositories you add in this way have been tested and are known to work on Ubuntu systems. Repositories that are not designed to work with your version of Ubuntu can introduce inconsistencies in your system and might force you to re-install.
I, and many others, run Ubuntu systems for years without any need to re-install.  We just have to carefully consider installing any software from "outside" the normal Ubuntu repositories for our particular release.

I am pleased that you have finally got your system working again and I sincerely hope you will be able to keep it this way ;-)

---

### Post by mastablasta on 2011-01-11
unless you NEED TO install certian software or if you even created it. then linux can become a mess and windows provides a better solution. because software has the necessary with them. everytime. so many times these are doubled (which is one of the reasons why windows programmes are so big compared to Linux).
 
basically if you need a newer software version you need to upgrade the whole system. ridiculous isn't it? epsecially if new system has some unresolved issues and might not work well on yoru maschine.
 
that's also the reason why Debian is OK for server but desktop - it has really old programmes. in windows you can regularly update programes without destroying the system.
 
as for .deb files - not all are Ubuntu compatible. you need to find the ones compatible with 10.04 if that is the version you use. another option is to compile. but again if you installed a programme and it's working fine i think you could also get away with locked package (you can lock the package in synaptic, so they won't upgrade or modify).
 
wine should be ok. just install it from software center. also any tools connected to it - install through center and it should work fine.

---

### Post by Yougo on 2011-01-11
there are ways of building/installing software in a self contained way, drawing from it's own private libraries and such. this way they don't touch your system at all, you can actually put them on a usb stick and run them from there if you want. i did it once with the release candidate of firefox 3.

don't ask me how i did that again though...
maybe someone can jump in and help here?

---

### Post by asuastrophysics on 2011-01-11
Thanks for your help Zill! I will read the "repositories" and "installing software" links very carefully. I thought I knew how to keep myself from breaking my computer, but I don't know enough about it apparently. I will read it, and prevent this sort of mishap in the future. You live and you learn.

---

### Post by egossett on 2011-01-11
I am a newbie and had to learn this as well. I installed 10.04 then came back to my new stable system a day later and got message to do update. Not realizing that i was really doing the upgrade to Maverick 10.10. which i did not want or need. Ok so I thought go with 10.10 but then i started getting messages and just did not understand what all of that was about so i wiped and re-installed 10.04 then changed the settings to  release upgrade NEVER. Til i know what is going on. I will stick with 10.04

Now I wish I could do this partition thing you mention here. But I don't feel confident to do this. 

I have not lost any data or files since this system is just to learn 10.04 and contribute. But I have 2 other computers I want to add Ubuntu as the main OS - need to learn more before I do that. 



> **anjilslaire said:**
>  
 
Otherwise, set Update Manager to never provide distro updates if desired: 
Update Manager>Settings>Updates>Release Upgrade>Never

Also, stick nto installing /home on it's own partition so you can wipe or reinstall the OS at will and never lose your data & settings.

---

### Post by egossett on 2011-01-11
Now I will have to make sure that I am observant of this advice.

> **Zill said:**
>  
A final word of advice is to be *very* wary of installing software that is not intended for your Ubuntu release, particularly if it installs additional dependencies, as this is *probably* the cause of your current woes!

Good luck.

---

### Post by Zill on 2011-01-11
> **egossett said:**
> ...Now I wish I could do this partition thing you mention here. But I don't feel confident to do this...
IMHO, having a separate /home partition makes things *far* easier if you ever need to re-install or upgrade the OS.

If you wish to do this then the best time is during installation of Ubuntu, when you can easily partition the HDD from within the installer.  As a minimum, you should create three partitions: / (root), /home and swap.  This is with a totally clean HDD.  If you also wish to keep another OS, such as Windows, then you will have further partition(s).

Personally, I have found that 10GB for the root partition, 1GB for swap and the rest for the home partition works fine for me.

If you wish to convert an existing installation to a separate /home partition then things are *slightly* more complex.  However, there is plenty of help available on this, such as [this guide]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

However, if you are trying this with a disk already containing data then I strongly recommend backing everything up elsewhere *before* re-partitioning.

---

