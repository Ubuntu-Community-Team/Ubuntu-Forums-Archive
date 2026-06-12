---
title: "Newb to Kubuntu, dunno where to start"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by kdefan on 2009-07-10
Hi like the title says I'm a complete newb to Ubuntu, coming from a land of (shattered) windows... (you get the idea lol) I've settled on Kubuntu right now, and I'm still considering Fedora KDE, so first question is, what are the significant differences between Kubuntu and Fedora KDE, in terms of functionality?

I also have an Athlon 7750, a WD Black 1TB and a GTX260, so I did a bit of research and found a bunch of themes like emerald and compiz that will actually put a load on my gtx260, but what are they, exactly? I'd like something to juice up my desktop with special effects, something that would make good use of my gtx260. Right now, I think the compiz would do the job, but I'm wondering if there are any others that are worth trying? I've watched some youtube vids with a bar on the bottom with icons that looks like the one found in OSX, and I'd also like to see that on my desktop :) I have no idea where to DL the 'official' versions of these, or how to install them, so please let me know how to do that too :p

I tried to install the proprietary drivers for my gtx260, but it just asks me to choose a program to open it with... which one should I use? When I was using Ubuntu, the 'install hardware drivers' thing installed the driver for me, but I still think I'd get better performance from a driver that I DL directly from the manufacturer's website, is that correct? There is also some desktop special effects option I found, and I receive an error message after trying to enable it... a little research shows that in the regular Ubuntu version, I'd have to install something. What is it exactly that I have to install for Kubuntu?

I'm also making a list of things to do once I get the basic stuff up and running :D I've got a small list of software that I want to install before I start using my system. Right now, I've got...
-gimp

and that's about all... please let me know if you guys have any suggestions for software to install. I'd also like a few more programs, but I'm not sure if they'd be compatible with Linux... and I have no idea how to use Wine lol. If any of these work in Linux, please let me know:
-Adobe Master Collection
-Microsoft Office 2007
-Paint.NET
-VLC player
-uTorrent
-Imgburn
-Nero
-any iso mounting software such as Daemon Tools
-any defrager such as JkDefrag
-System monitoring programs such as OCCT, cpu-z, hwmonitor, etc.
-and of course, games. I know that I can run just about any Source engine game (HL2 and stuff) with WINE, but I'd also like some of the popular stuff such as Crysis, COD, BF, NFS, GTA, etc. If I get these games working in Kubuntu, I won't have to ever use Windows again :D

Sorry that's a lot of questions for a 1 bean green freshman, but once I get Kubuntu juiced up with a nice GUI and games, I'll be here to stay for sure :) Thanks for all your help guys

---

### Post by Ji Ruo on 2009-07-11
I can't personally help with most of that, but this might be a useful resource for you:

[Unofficial Kubuntu Guide]("http://kubuntuguide.org/Jaunty")

Note the sections on Desktop effects, Wine (etc) and VLC Media Player.

---

### Post by Cato2 on 2009-07-11
Kubuntu vs. Fedora KDE - no idea really, probably no dramatic differences.  Biggest difference will be the Ubuntu vs. Fedora base - Ubuntu is supported for longer and has stable LTS versions (3 or 5 year support lifetime, desktop or server respectively) whereas Fedora is only 12 months or so, and you must use RHEL/CentOS for longer support.

Compiz stuff - should work on KDE but some have reported GNOME works better.  KDE 4.x, since Ubuntu 8.10, includes some 3D effect stuff built in without Compiz, try it out.

OSX bar at bottom - search for "AWN ubuntu"

Apps - most should be in repository, use the KDE add/remove programs option, or the KDE package tool I never use, or install Synaptic which is good. Recommend you search for the "open source alternatives" website which shows you which OSS apps correspond to Windows apps you use.

-Adobe Master Collection - no idea

-Microsoft Office 2007 - try OpenOffice latest version but the 2007 support is still weak - best if you can use 2003 formats or native ODF

-Paint.NET - Krita perhaps or GIMP, there are lots of apps here

-VLC player - same, or try Totem, Mplayer or others.  VLC is pretty capable.

-uTorrent - search for torrent apps, I use KTorrent but there are many others

-Imgburn - probably K3B which is great

-Nero - K3B

-any iso mounting software such as Daemon Tools - built in, just google for "mount -o loop iso format", and probably KDE's Dolphin file manager lets you do this too 

-any defrager such as JkDefrag - not required - ext3 and other Linux filesystems simply don't get fragmented to any noticeable degree.  If you have a very volatile filesystem (think mail server for a whole company) then it's good to put that on a separate filesystem but this is extreme case.

-System monitoring programs such as OCCT, cpu-z, hwmonitor, etc. - try GKrellM which is nice, also GNOME's own system monitor tool, and KDE has a process monitor.  Also search for Hardinfo and HW Lister.

- Windows games - Try Wine - and specifically PlayOnLinux, Wine Doors and winetricks for easy installations.  

You may want to grab your Windows fonts and add them to Ubuntu - this is easily done with a google, recommend you put them under /usr/local.

The Ubuntu hardware drivers are actually from the manufacturer, so don't spend time on this unless you are having a performance problem.  Compiz and 3D games should just work normally.

General tip - put all the non-standard stuff you install (not from Ubuntu repositories) under /opt (for big packages, e.g. Google Picasa for photos) or /usr/local (smaller stuff that is compiled from source, or misc stuff such as fonts).

Hope that helps.  Do get onto the Kubuntu site and Google for 'xyz HOWTO', which is the Linux convention for step by step guides.

---

### Post by carml on 2009-07-11
> **Cato2 said:**
> 
You may want to grab your Windows fonts and add them to Ubuntu 


You can accomplish this task typing on a terminal```
sudo apt-get install ubuntu-restricted-extras
``` followed by your password.So you'll install also other common searched softwares like Sun Java Virtual Machine etc.

---

### Post by kdefan on 2009-07-11
Hey thanks so much for replying you guys :D that's a lot of text :

The Kubuntuguide is pretty big, I'll spend tomorrow reading it and it'll probably solve just about all my questions, but I'm still confused about where to save stuff... In bad ol' days of Windows, I installed my non-performance related software (such as MS Office) into the default 'Program Files' folder, and I installed my games in a different partition. My WD Black 1TB has 3 platters and I've stroked them, so it looks kinda like this from outside to inside of platters:

1st platter - 6gb unused, 4gb swap, rest is ext4 data '/home' (should I use ext4?)
2nd platter - 20gb unused, 20 kubuntu '/', rest is ntfs storage
3rd platter - 50gb unused, 50gb kubuntu games, rest is ext4 storage

So I've basically maxed it out at 4 ext4 partitions and 4 (planned) ntfs partitions... I haven't formatted them yet so they're stilled marked as free space. I'm still debating if I should install Win7 in the 'unused partitions'. If I can get my fav games installed on Kubuntu, I won't have any use for Win7 anymore.

I'm still kind of confused about where to put my files... so when I install something from the repositories, can I choose to save it in a specific mount point? Should I be saving programs such as GIMP, Compiz, (and if I can get them working with WINE) Adobe Master Collection and all my games in /opt? Where should I save data files such as movies and photo albums, and does it make a performance difference when I save installations in a specific mount point? So basically, which mount point does Kubuntu leave for my games, where I can mount a partition and no Kubuntu files will be in it? Not sure if you guys can understand what I mean... basically, I just want all my games and things that need performance such as swap to be on the outside of my disc, where data transfer is faster :)

And about the drivers, are they exactly the same if I manually DL them from the manufacturer's site? In the past when using XP, installing the drivers XP recommended just accelerated video performance and gave me to correct resolution, but when I installed the drivers from the manufacturer's site, I got a new control panel with a slew of options to customize my display output... I'm just curious if I'd get the same results in Kubuntu.

And carml, what exactly does that code do? Can I get them from the repositories?

Thanks so much for the great replies!

---

### Post by Ji Ruo on 2009-07-12
> **carml said:**
> You can accomplish this task typing on a terminal```
sudo apt-get install ubuntu-restricted-extras
``` followed by your password.So you'll install also other common searched softwares like Sun Java Virtual Machine etc.

Actually it's kubuntu, so shouldn't it be```
sudo apt-get install **kubuntu**-restricted-extras
```? Not sure how much difference it makes...

kdefan, this command will install all of the restricted extras (stuff which isn't open source, but you'll probably need) on your computer in one go - java, mp3 playback, support for flash, the microsoft fonts that have been mentioned etc etc etc. As you will see in that unofficial guide, if you want DVD playback of region encoded DVDs you will need to put in one more command (follow the link in the restricted-extras section then copy and paste).

---

### Post by carml on 2009-07-12
I thought there was only a package,I'm not aware if there's a particular vesion for Kubuntu.:-k

---

### Post by Cato2 on 2009-07-13
> **kdefan said:**
> Hey thanks so much for replying you guys :D that's a lot of text :

1st platter - 6gb unused, 4gb swap, rest is ext4 data '/home' (should I use ext4?)
2nd platter - 20gb unused, 20 kubuntu '/', rest is ntfs storage
3rd platter - 50gb unused, 50gb kubuntu games, rest is ext4 storage

So I've basically maxed it out at 4 ext4 partitions and 4 (planned) ntfs partitions... I haven't formatted them yet so they're stilled marked as free space. I'm still debating if I should install Win7 in the 'unused partitions'. If I can get my fav games installed on Kubuntu, I won't have any use for Win7 anymore.

I'm still kind of confused about where to put my files... so when I install something from the repositories, can I choose to save it in a specific mount point? Should I be saving programs such as GIMP, Compiz, (and if I can get them working with WINE) Adobe Master Collection and all my games in /opt? Where should I save data files such as movies and photo albums, and does it make a performance difference when I save installations in a specific mount point? So basically, which mount point does Kubuntu leave for my games, where I can mount a partition and no Kubuntu files will be in it? Not sure if you guys can understand what I mean... basically, I just want all my games and things that need performance such as swap to be on the outside of my disc, where data transfer is faster :)

And about the drivers, are they exactly the same if I manually DL them from the manufacturer's site? In the past when using XP, installing the drivers XP recommended just accelerated video performance and gave me to correct resolution, but when I installed the drivers from the manufacturer's site, I got a new control panel with a slew of options to customize my display output... I'm just curious if I'd get the same results in Kubuntu.

And carml, what exactly does that code do? Can I get them from the repositories?

Thanks so much for the great replies!

The repository stuff just goes where it's supposed to go - you can't really control this but then it's not usually large like a commercial 3D game (but there are some large games in repositories).  The Ubuntu games should go under /usr/games -  if you install some large games you'd need to (1) stop using /usr/games by closing any games, (2) create a new directory on new mountpoint, e.g. /opt/games, to replace it and (3) move the files across preserving permissions - simply 'mv /usr/games /opt' should work but be sure you have enough space (du -k /usr/games) and don't interrupt it.

Some proprietary drivers e.g. Nvidia come with a control panel - easiest to install that via envy (google for it).  However that's the exception, the vast majority of drivers are open source and built into the Ubuntu Linux kernel - this makes them much higher quality as bugs can be fixed more easily by the whole kernel team.  In fact the Nvidia drivers, though good, can be a source of crashes for some people, and there's a team reverse engineering the Nvidia hardware to write new drivers (nouveau).

For data, I would simply have a /home partition that is very large, enough for all movies etc.  Some people prefer to create a /data partition for all music, movies, etc - it's up to you, and in some ways that's more flexible.

For large apps, I use /opt as mentioned - however that's only for non-repository apps and I try to keep these as few as possible.  I install a lot of apps, and have only 7 under /opt - and 2 of those are Firefox and Thunderbird as I like to have the latest versions without waiting for Ubuntu updates.

You need to make sure you create a partition and mount /opt under it.  Something like this in /etc/fstab, but Kubuntu may have a tool under the control panel thing for this:

```

LABEL=opt  /mnt/opt           ext3    noatime,barrier=1,errors=remount-ro        0       2

# Windows NTFS - normally /dev/sda2, main hard disk.
UUID=424C1CF34C1CE387 /mnt/win      ntfs-3g     defaults,locale=en_US.utf8         0       0

# Shared FAT32 - normally /dev/sda7, main hard disk
LABEL=shared /shared      vfat     defaults,utf8,uid=1000,gid=1000      0       0

```

The LABEL stuff is optional, you can use UUIDs which Ubuntu generates for you normally.  Or use device names, but beware as these can sometimes change if you plug in a USB drive/stick.

---

### Post by carml on 2009-07-13
What you download from the repository (read via Synaptic or similar) get installed automatically on the proper place,for what concern your personal data (videos,photos etc) you can save them under your home directory.
Gimp is already present when you install *buntu.
Generally every OS uses its own drivers so,apart a particular wireless card or graphic card,you don't need to download any driver from the manufacturer.
The code I suggested you to type,maybe corrected as [...]kubuntu-restricted[...] will install some most wanted applications such as Sun Java Virtual Machine,Microsoft's fonts etc.
I hope I nailed all your questions,if I missed something I think you'll forgive me ;) .

---

### Post by Ji Ruo on 2009-07-13
> **carml said:**
> I thought there was only a package,I'm not aware if there's a particular vesion for Kubuntu.:-k

There is, I used it to install the restricted extras package on my system. I'm not sure what problems may occur if you omit the 'k', if any. Maybe you have to add a whole lot of gnome packages to your system for dependencies?

---

### Post by nynoah on 2009-07-13
If you are a new user, I would stick with Kubuntu and leave Fedora for a time when you have more experience.  Fedora is more bleeding edge and Ububu/kubuntu has more options for programs.  Atleast that is my opinion.

---

### Post by kdefan on 2009-07-14
For that code, I'll try it with a 'k' and if it doesn't work I'll try 'ubuntu'. For the partitions, is it possible to make more than 4? I'd like to have a '/', '/home', '/data', '/opt' and swap, and for Win7, I'd like to have a partition for page file, OS partition and Games partition. Is it possible to have this many partitions? Would you guys recommend me to use Parted Magic? What size should each of those mount points/partitions be at least, and should they be ext3 or ext4? I'm in Toronto, so I rarely get outages, but it does happen during thunderstorms...

Hey cato2, I have no idea what those mean :p what's '/etc' for, and what does '/dev/sda' and 'LABEL=shared /shared      vfat     defaults,utf8,uid=1000,gid=1000' mean?

Thanks guys! :D

---

### Post by carml on 2009-07-15
As far as I know,you can have got only for primary partitions on a disk,but any of them (at least all) can be extended partitions,think to them as boxes the number of bigger is limited to four,but inside (if are extended) you can fit up to fifteen partition for each extended partition.
I hope my explanation is clear and can help you decide how to partition your disk,if you need more help just ask and someone will answer you. :)
P.S. yes choosing to install some Kubuntu package over Ubuntu (or vice-versa) will install also the strictly needed packages.

---

### Post by perspectoff on 2009-09-09
I learned a lot from

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

about partitioning ideas.

There can be four primary partitions, one of which can be an extended partition with unlimited logical partitions. 

It is best to make the extended partition the last partition on a hard drive. All linux partitions are best placed into logical partition within the extended partition.

Both Kubuntuguide.org and Ubuntuguide.org have a wealth of information.

---

