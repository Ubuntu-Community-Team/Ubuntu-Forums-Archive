---
title: "My fears with using Ubuntu"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Yautja_Cetanu on 2010-10-21
So I'm currently using Windows 7 64-bit on a Sony Vaio F11. I've had some problems with it and so I reformatted and thought I'd try ubuntu again (I've been trying to get it working for about a year with my various computers I'd had access to).

Now I've read a bunch of threads about the issues surrounding my laptop:

[http://ubuntuforums.org/showthread.php?t=1587885&highlight=Sony+Vaio+F11](http://ubuntuforums.org/showthread.php?t=1587885&highlight=Sony+Vaio+F11)

[http://ubuntuforums.org/showthread.php?t=1470822&highlight=Sony+Vaio+F11&page=5](http://ubuntuforums.org/showthread.php?t=1470822&highlight=Sony+Vaio+F11&page=5)

Amongst others. It seems there are no real fixes to getting Nvidia drivers on ubuntu 10.10. However out of the box ubuntu seems to work on my laptop just without the proprietary drivers. So here are my fears:


1) This is a work machine, I can't lose any data and I'm going to be working on websites so lots of data is tucked away in databases.

2) Does ubuntu have an easy way of backing everything up so I can reformat ubuntu and get everything back? I have seen complicated ways but the majority of the reasons why I need to reformat ubuntu are due to my own stupidity (I've tried multiple times install ppas to get nvidia drivers working)

3) Some of the methods that make my laptop work with ubuntu require downloading the .run files from the nvidia websites. I have been told the latest drivers work. But I've been told .run files ruin things? How would I have known this? Is it really that dangerous to use run files?

4) It seems like in order to learn how to use ubuntu. I am going to have to make alot of mistakes and try things out. However in order to try things out, I have to actually use ubuntu. In order to use ubuntu, I'm going to have to work on it with files I cannot lose. But because I cannot lose these files, I can't afford mistakes?

Does this mean I can literally never move to linux?

---

### Post by spiky001 on 2010-10-21
Hi if you install and have a seperate partition for home then if you have to reinstall the home will stay and work with the new insatll is this what you mean

---

### Post by trikster_x on 2010-10-21
One thing I like about ubuntu or any nix distro is that you can install it on multiple partitions.  You can have a small partition for playing around with new programs and getting used to the terminal.  Another that holds your main install for work.  A separate home partition would ensure that, should you do something to mess up a root folder, you don't lose any of your personal data.

I personally keep a partition for the root portion of Ubuntu, a partition for my home folder, and a third partition specifically for personal files.  That way I know if I mess something up on Ubuntu, I can reinstall at any time.  If I decide to switch distros, my personal files don't have to be backed up and moved from one drive to another.  If you do it this way, it is best to put 10GB for the main install, 10GB for /home, and the remainder of your drive for personal files.  If you want to have a partition to play with Ubuntu, I suggest you make that one 15GB partition and set it up with /home on the same partition.  

[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome") is a good guide on how to set up home on a seperate partition while installing Ubuntu.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") Official guide to partitioning in general.

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087") is a guide to backing up data in Ubuntu with a good explanation of what the terminal commands do.

as for .run files, I have never personally had to use one.  But from what I have read, most of the problems stem from people not understanding that files are not executable by default.  [https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage") is the official documentation for installing .run files, and there is no mention of anything dangerous happening.  Just make sure the file is from a source you trust since it will probably require root level access to run.

Any file that requires root access to run can be dangerous if you aren't 100% certain of the source of the file.  This is simply because, while there aren't many, some viruses for linux do exist.  The reason they don't proliferate is because you must give them ROOT access to do irreparable damage to your system, which means entering your password.  As long as what you are running comes from or has been tested by a reputable source, there should be nothing to worry about.

And remember, Ubuntu is not Windows.  So when you are looking for a way to fix a problem, or a guide for doing something, a quick google search will usually result in a plethora of information, rather than sending you to a company built troubleshooter that doesn't work or a knowledge base that doesn't actually contain the info you are looking for.

---

### Post by LowSky on 2010-10-21
1. Back up all important data. When installing Ubuntu create a seperate partition for /home. That way if the system goes up in flames all your user data is safe.
2. Do not experiment with new OSes on Production (WORK) machines. Too many people who know too little have left questions on what happened to their data because they accidentally formated the entire hard drive.
3. follow this for newest Nvidia drivers
open a terminal and copy and paste the command one at a time
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```

---

### Post by QIII on 2010-10-21
First and foremost:  Whenever you do ANYTHING, back up the data you can't afford to lose.

Again:  Back up the data you can't afford to lose.

Did I mention to back up the data you can't afford to lose?

I use a separate /home partition so that I can do a clean install when new versions come out.  Doing things that way makes it easy to just use manual partitioning and simply not format /home.

But I still back up my entire /home partition.  Hidden folders and all.  I even use a technique for listing all of my installed programs (other than third party) so they can be reinstalled without fuss when the reinstallation is done (different topic, you can probably find a number of posts on the subject.)  I also throw in some files like my hosts file to make it easier to get my networking back up.

Again:  You should ALWAYS back up.  Take nothing for granted.

---

### Post by aysiu on 2010-10-21
> **QIII said:**
> First and foremost:  Whenever you do ANYTHING, back up the data you can't afford to lose.

Again:  Back up the data you can't afford to lose.

Did I mention to back up the data you can't afford to lose?

...

Again:  You should ALWAYS back up.  Take nothing for granted. I agree with this advice wholeheartedly.

Even if you *aren't* installing Ubuntu, you should regularly back up data you can't afford to lose.

A large external hard drive (250 GB) is about US$60 or so. Is your data that important to you? That US$60 shouldn't be that much of an investment, then. If you're really short on cash, give up coffee for a few weeks. Seriously.

Back up. Always back up.

Make a CloneZilla backup, too.

---

### Post by ivarn on 2010-10-21
Since your pc is a work machine, you should install a LTS (long time support) version of ubuntu. Version 10.04 is an lts version. Upgrade it ONLY for lts versions (v12.04, 14.04 etc). LTS versions doesn't include the beta (not fully tested) features that can make the OS more unstable or buggy at times.

---

### Post by leclerc65 on 2010-10-21
Does your Vaio have a CD Drive, or do you have access to an external CD drive ?
There is a software named G4L (Ghost for Linux - google for it) that can backup the whole hard disk to an external HDD. I once recover my Acer One (Windows, Ubuntu, and all ...) painlessly after messing it up badly. Backup is a pain though, but it can be done overnight (my Acer has only 120G).

---

### Post by aysiu on 2010-10-21
> **leclerc65 said:**
> Does your Vaio have a CD Drive, or do you have access to an external CD drive ?
There is a software named G4L (Ghost for Linux - google for it) that can backup the whole hard disk to an external HDD. I once recover my Acer One (Windows, Ubuntu, and all ...) painlessly after messing it up badly. Backup is a pain though, but it can be done overnight (my Acer has only 120G).
I'd recommend CloneZilla instead, as backups are really fast and do not take overnight. It'll ghost only the actual written data (so if you have a 120 GB hard drive and you're using only 43 GB of it, the image will be about 43 GB large).

---

### Post by poodoopealeoaph on 2010-10-21
well one thing that I've had an issue with with ubuntu is that when I just had it running dualboot with windoze 7, it tried to update. No big deal right? well it turns out that it installed half the updates correctly, removed some files that shouldn't be removed from the registry, and installed the replacement files onto an external HD that I had plugged in. So.... I went to Kubuntu. Much more solid than it used to be. You should give it a shot. Especially if you are coming from windoze. It is a very similar format

---

### Post by RedRat on 2010-10-21
I would second the idea raised by ivarn above, go with 10.04 LTS. Constantly updating versions, though tempting, can introduce instabilities in your system. This is particularly true if the machine is going to be used in a business environment, you need to be prudent here.

---

### Post by LowSky on 2010-10-21
> **ivarn said:**
> Since your pc is a work machine, you should install a LTS (long time support) version of ubuntu. Version 10.04 is an lts version. Upgrade it ONLY for lts versions (v12.04, 14.04 etc). LTS versions doesn't include the beta (not fully tested) features that can make the OS more unstable or buggy at times.

Actually when 10.04 was release a few programs were still in beta, like MythTV.

LTS doesn't mean more stable, it just means longer support.

I have no idea where people keep getting the idea that a LTS is more stable.

---

### Post by sailorboy on 2010-10-21
As done said- MAKE BACKUPS. An alternative is to make an ubuntu thumb drive with persist. Slow to boot but functions rather well- that would give you ubuntu without alering the HD. Just a thought.

---

### Post by trikster_x on 2010-10-21
> **LowSky said:**
> Actually when 10.04 was release a few programs were still in beta, like MythTV.

LTS doesn't mean more stable, it just means longer support.

I have no idea where people keep getting the idea that a LTS is more stable.

It's not that it is necessarily more stable at launch, it is just a better option for stability in a work environment than upgrading versions every 6 months.  I have been using Ubuntu since 8.04 and I have one machine that is going to stay with 8.04 until it dies, for the simple fact that I know I can boot into it and it will work with all my hardware and software.  My other comps however get upgraded to new versions regularly.  One on release day and the other after I have worked out all the bugs that come with a new version.  And there are always bugs. 

When I upgrade the first comp, I always have problems with at least one application I use on a regular basis after the first few of my update cycles.  The second one almost always has a driver problem or two.  But my old faithful always boots and runs all programs normally.

---

### Post by su-37 on 2010-10-21
as for backing up you could just sync the folders using ubuntu one. right click and itll be there.

---

### Post by mastablasta on 2010-10-22
Debian stable is even more stable and supported for quite a long time.

---

### Post by ivarn on 2010-10-22
> **LowSky said:**
> Actually when 10.04 was release a few programs were still in beta, like MythTV.

LTS doesn't mean more stable, it just means longer support.

I have no idea where people keep getting the idea that a LTS is more stable.

True, but longer support also means they will use more time with that version, to fix its bugs and such. That is why an LTS version would be the best alternative for a business pc.
I don't literally mean LTS means more stable, but an LTS version means more stable over time.

> **mastablasta said:**
> Debian stable is even more stable and supported for quite a long time.
But less newbie and user friendly.

And yes, ubuntu one is a perfect backup tool (up to 2gb), but if you need to backup huge files and such then you should go for VDrive.com. They give you 50gb for free. and if you need more, their prices are friendly.

---

### Post by Yautja_Cetanu on 2010-10-22
Thanks for all the replies!

The problem with going with 10.04 is that it didn't work with my dual screens at all. With the nvidia drives I could only use the external display and with stock drivers I could only use my laptop display. So thats why I've gone for 10.10 because it works.

Again, I've found that whilst there are loads of helpful tutorials out there. There are too many! Also they give conflicting advice (For example I saw a screencast of how to install a .run file from nvidia's website direct. But been told that is bad because I need a PPA as .run files are hard to update/install I've also read loads of tutorials on how to install a PPA but I could never get it to work.

The problem with some tutorials that rely in "common sense" is that I can't tell which direction to have common sense. I have no idea if I did something wrong with the ppa, if the problem is with nvidia (I read it isn't) or with ubuntu or with the way i enabled drivers afterwards. It seems impossible to find which information to listen to (apart from helpful forum posts, thanks guys!)

---------

I'm going to try clonezilla. I have a 1TB external Hard drive using Windows Backup (which seems to work pretty well). I also have a 320gb external hard drive to back up important stuff again and I have mozy home (online backup for windows)
One idea I have is this. I have a 500GB hard drive.

I'm going to format one drive in NTFS for Winodws 100GB
I'm going to format another drive for ubuntu 70GB using its file format
Then I'm going to format another drive for all my files to share between both OSes. I'll put music, Documents, videos, etc there

I think I'll try that anyway (for music) but can I store my /home/ and /etc/ directories on this NTFS partition?

----------

Final question. Is it that big a deal that ubuntu only works without the nvidia drivers?

---

### Post by oldfred on 2010-10-22
For any data you want to share should be in the NTFS partition. But NTFS does not support Linux permissions and ownership so no system files can be in NTFS. You can link folders into /home so it looks like data is in your /home but /home has all the (mostly hidden with.) user folders that make up your configuration.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by JPorter on 2010-10-22
> **trikster_x said:**
> It's not that it is necessarily more stable at launch, it is just a better option for stability in a work environment than upgrading versions every 6 months.  I have been using Ubuntu since 8.04 and I have one machine that is going to stay with 8.04 until it dies, for the simple fact that I know I can boot into it and it will work with all my hardware and software.  My other comps however get upgraded to new versions regularly.  One on release day and the other after I have worked out all the bugs that come with a new version.  And there are always bugs. 

When I upgrade the first comp, I always have problems with at least one application I use on a regular basis after the first few of my update cycles.  The second one almost always has a driver problem or two.  But my old faithful always boots and runs all programs normally.

I have been using Ubuntu for my primary work PC in a full office environment through every single version since 8.04.  I have had ZERO problems with stability, and I stress the box every single day.

---

### Post by Megaptera on 2010-10-22
Another backup option to produce a CD/DVD is Remasterys. Good guide from here:

[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by JPorter on 2010-10-22
OP... you should be able to get the proprietary drivers working on your VAIO by adding two lines to your xorg.conf file...

[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

---

### Post by trikster_x on 2010-10-22
> **JPorter said:**
> I have been using Ubuntu for my primary work PC in a full office environment through every single version since 8.04.  I have had ZERO problems with stability, and I stress the box every single day.

Don't get me wrong, most of the problems I have had have been easy fix stuff; a .conf file here, a driver file there. Definitely nothing on the level of the various Windows versions I have dealt with.  But for some (especially those who are unfamiliar with troubleshooting a computer problem), even a small problem can turn into 1-2 days of downtime, which can be unacceptable when there is a deadline looming overhead.  As such it is always good advice to someone not familiar with Ubuntu or Linux in general to stick with an LTS, at least until they know how to find and use the information they need.

---

### Post by leclerc65 on 2010-10-27
> **aysiu said:**
> I'd recommend CloneZilla instead, as backups are really fast and do not take overnight. It'll ghost only the actual written data (so if you have a 120 GB hard drive and you're using only 43 GB of it, the image will be about 43 GB large).
Clonezilla is indeed better than G4L.
Thanks for the tip.

---

### Post by Irony on 2010-10-27
> **Yautja_Cetanu said:**
> 2) Does ubuntu have an easy way of backing everything up so I can reformat ubuntu and get everything back? I have seen complicated ways but the majority of the reasons why I need to reformat ubuntu are due to my own stupidity (I've tried multiple times install ppas to get nvidia drivers working)
Yes do this to copy your entire distro to some external drive;

```
sudo cp -ax /. /media/nameoffolder/.
```

In the event of a failure simply format your current partition (using a live CD) and copy the contents back like this;

```
sudo cp -ax /media/nameoffolder/. mountpoint/.
```

This is so simple that hardly anybody believes it will actually work so hardly anybody uses it.

---

### Post by ezsit on 2010-10-27
> But because I cannot lose these files, I can't afford mistakes?


Get a second machine, a cheap, used desktop on ebay will cost less than $100, and play on that. If your work machine needs to stay trouble-free why introduce trouble? Linux is great once you know how to use it. Learn how to use it without risk.

---

