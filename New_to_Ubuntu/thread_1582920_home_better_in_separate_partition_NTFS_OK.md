---
title: "/home: better in separate partition? NTFS OK?"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by sallam on 2010-09-27
Greetings
I'm about to re-install ubuntu. Last time it deleted all my hard disk when I inoccently selected the "side-by-side" deceiving option.
Anyhow, I've been reading a lot before I re-install this time. There is a question that I need your help with:
Is it better, before installing. to create a separate /home partition?
and if yes:
[LIST=1]
[*]Is it ok to make /home in the same NTFS patition that I save my data in, when I'm using Win7, so that all my data can be shared in one data storage partition?
and If during installation I selected the NTFS storage partition, will uuntu format it and delete all the data in it? or leave it in NTFS and just use it as it is?


[*]Or  is it better to create a new ex4 partition for  /home?


[*]Or is it better to not create /home, and instead, after installtion is finished, I delete /home directories and use the ntfs-config tool to point ubuntu to use the same directories in the shared storage NTFS partition?
[/LIST]

I've read different approaches from these resources:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)
[https://help.ubuntu.com/community/DiskSpace#Separate](https://help.ubuntu.com/community/DiskSpace#Separate) /home

Could someone please suggest the best solution?
I hope I can share the same data in both Win7 and ubuntu.. while at the same time make sure ubuntu is running  with speed and no problems.

---

### Post by Paqman on 2010-09-27
> **sallam said:**
> 
Is it better, before installing. to create a separate /home partition?

It allows you to do a full reinstall without losing any of your application settings. If that sounds like something you want to do, then it'll be a useful way to set your machine up.

> 
Is it ok to make /home in the same NTFS patition that I save my data in, when I'm using Win7, so that all my data can be shared in one data storage partition?


I haven't tried it, but AFAIK you do need to use one of the proper Linux filesystems.

You don't have to store your data in /home if you don't want to. Having your settings in /home and your data on a shared partition is fine.

---

### Post by philinux on 2010-09-27
NTFS is no good for /home as it has no linux permissions. Ext4 is the way to go.

I've had home on it's own partition for 2 years now and I reinstall every 6 months, it's a doddle.

---

### Post by 0N3 on 2010-09-27
I dont use Windows myself but my advice is definitely make a /home partition i configure mine  as follows

/ (10-20GB) root partition Ext4

/swap 4GB swap partition

/home as the rest of my partition Ext4

This way when i have to reinstall Ubuntu I only have to format the /root partition thus keeping all my files, pics, docs, movies program settings bookmarks intact never loosing anything I love this about Ubuntu whereas in windows you have to format the hole partition and lose everything if no backup is made which is often the case this also doesn't mean you shouldn't make backups of important files weekly.

---

### Post by sallam on 2010-09-27
Many thanks for the prompt replies.
I'm a bit confused. What exactly does /home used for?
Is it used to install programs, so that when I reformat and re-install ubuntu in root partition, my programs are still working?
or does it only save programs settings and files that we create with them?
When we re-install ubuntu, or install a new version every 6 months, do we have to download and install all pachages and programs again?

and if so, is it ok to create a separate /home ex4 partiton, but delete documents directories to let ubuntu save my data/pics/music/files..etc in the Win7 ntfs shared partition?

---

### Post by philinux on 2010-09-27
Also see this re Swap seeing as you're reinstalling.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by 0N3 on 2010-09-27
Its used to store all your personal files pics, music, vids ect........ and configuration files of programs such as compiz preferences, firefox bookmarks ect....... so if you ever reinstall ubuntu you dont lose any of these settings it remembers it all its extremely handy feature

---

### Post by Paqman on 2010-09-27
> **sallam said:**
> 
I'm a bit confused. What exactly does /home used for?


It contains the settings for all your apps. It doesn't contain the apps themselves. For example, it would contain all your browser bookmarks. So if you reinstalled your browser, it would have all the bookmarks the same as before.

It can also be used to store any data you want. Or you could put your data elsewhere. Up to you.

---

### Post by mastablasta on 2010-09-27
> **Paqman said:**
> It allows you to do a full reinstall without losing any of your application settings. If that sounds like something you want to do, then it'll be a useful way to set your machine up.
 
 
 
related but a bit more offtopic question - why if this is "better" solution this is not done by default? or better yet give the simple option (tick box) in the installer for the user to make a separate home partition for their needs.

---

### Post by Paqman on 2010-09-27
> **mastablasta said:**
> related but a bit more offtopic question - why if this is "better" solution this is not done by default?


Because officially you don't need to do a full reinstall every six months, but a lot of users like to do it anyway. If you're not reinstalling, there's little advantage to a separate /home, except for distro-hopping I guess.

> 
or better yet give the simple option (tick box) in the installer for the user to make a separate home partition for their needs.

This I tend to agree with, although I guess the thinking is that anyone with a separate home will be using the advanced partitioning tools in the installer for every subsequent install anyway, so why not use them the first time too?

---

### Post by QLee on 2010-09-27
[QUOTE=sallam]...
I've read different approaches from these resources:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)
[https://help.ubuntu.com/community/DiskSpace#Separate](https://help.ubuntu.com/community/DiskSpace#Separate) /home

Could someone please suggest the best solution?
I hope I can share the same data in both Win7 and ubuntu.. while at the same time make sure ubuntu is running  with speed and no problems.[/QUOTE]
I'd be happy to suggest what I consider the best solution for you.

1st, I'd probably use an Ubuntu community document if I was doing it on an Ubuntu system.
2nd, I suggest you install a released version, you've already been having lot of troubles trying to use 10.10 and the beta software is more suited to people who can troubleshoot problems and fix them or file trouble reports.

---

### Post by julio_cortez on 2010-09-27
> **mastablasta said:**
> why if this is "better" solution this is not done by default? or better yet give the simple option (tick box) in the installer for the user to make a separate home partition for their needs.
I for one would suggest having a separate /home, and it's something that I do on every machine I install Ubuntu on (apart from the cases I'm asked not to do so).
*By the way, I also have a NTFS /media/Data partition where I store the most of my data to be accessed also from Windows 7* :D

But, probably, the installer is meant to be as "user friendly" as possible I guess, so dealing with partitions maybe is considered too "advanced" for the unexperienced user that is only asked to follow a very simple course to get the work done with the "default" setup.

I second the tick box idea, though. Despite not being it too difficult to work out the partitions manually, maybe a tick box that "takes care" of creating a separate /home will be welcomed by the unexperienced user of the example above *provided that he's given the information about why a separate /home will be better in case of reinstall*.

---

### Post by mastablasta on 2010-09-27
yes to me it is a bit too advanced and confusing. on my second install i wanted to do a separate home (i know i can still do it). but i couldn't undertstand what exactly does it want me to do. so in the end it was erase all and auto partition which went well.
 
separate home is not just for fresh install instead of upgrade. it also holds user data such as downloads, pictures and stuff (folder made by default i believe). in fact anything you do you are offered to save it on your home partition. it sort of acts like My Documents in windows.
 
Now what i do in windows is always have a separate partition only for data my data. because if something goes wrong with the OS (power goes out, files get corrupted, upgrade failed...) i can just format the OS partition and reinstall the whole thing. been there, done that... separate partition rocks. 
 
and linux has the option to have it all there - safe from the OS corruption. so why not make it easy for the users to do it like that? i mean is there really any drawback? cause it could be one that i probably don't know. maybe problems if user wants encrypted Home?!

---

### Post by Vaphell on 2010-09-27
> why if this is "better" solution this is not done by default? or better yet give the simple option (tick box) in the installer for the user to make a separate home partition for their needs.

This is more a psychology thing than anything else. Separate home is better but that doesn't mean people want to see that, ever, especially in the 'entry level' distro tailored for beginners. People in general are used to the idea that they get their computers with systems preinstalled or the installation process of anything can be done with 5 braindead 'next's max and they are perfectly happy with their windows laptops where they have exactly 0% of influence on how hdd is partitioned. You show people the word 'partition' and suddenly 90% of them are out of their comfort zone and start to think 'omg, linux is hard and confusing' so they simply give up.

---

### Post by julio_cortez on 2010-09-27
> **mastablasta said:**
> separate home is not just for fresh install instead of upgrade. it also holds user data such as downloads, pictures and stuff (folder made by default i believe).Yeah, sorry if I explained bad.. I meant that having a separate /home will be useful because you could still access your downloads/documents/music and so on even if you reinstall :)

By the way, you're kind of right: /home is rather similar to the Users folder you have in Windows 7 :)

---

### Post by cpmman on 2010-09-27
If you want /home in a separate partition some microcomputer manufacturers purposely create all 4 primary partitions to prevent simple "alongside" installations.  I had to make the 3 dvd reinstall discs and then used Windows to delete the reinstall partition, shuffle and reduce the remaining partitions to create unclaimed space for a gParted extended partition which contains /, /home,swap and lots of space for other / installs sharing, and/or upgrades etc.

---

### Post by bsalem on 2010-09-27
A general reply:

Although Ubuntu can read/write to NTFS, it isn't as safe as using NTFS with Windows. Not long ago you couldn't write to NTFS using Linux. /home/username should be on native Linux filesystem separate from NTFS. It is for your files and personal configurations under Linux. If you create files that need to be shared, it is better to copy them to NTFS if they must be created under Linux.

Note that Windows knows nothing by itself about Linux filesystems unless there is some third-party driver or app that can mount a Linux filesystem. Microsoft does not go out of its way to make data created on a Windows system exportable to another OS. If an app on Linux can read a file created on Windows, the reverse may not be true. Open Office can read DOC files created by Office/Word, but even though they are put on an NTFS filesystem after being modified by OOo, they may not be fully supported on Windows, for example.

---

### Post by The Cog on 2010-09-27
More than that, you **cannot** get /home to work on an NTFS partition - the permissions aren't right because NTFS can't store permission properties, and so lots of things don't work.

/home is used to house the home folders for each user, which is where all their documents and application settings are stored.

I suspect the reason that the basic installer doesn't offer to create a separate /home is the difficulty of deciding how big both / and /home should be. You can't ask the user this - many windows users don't even know what a partition is, and certainly don't know how big the Linux partitions need to be. IN the advanced setup, that's all there to be done manually of course, although that is a whole other level of difficulty.

---

### Post by sallam on 2010-09-27
Thanks to all your valuable advices, I've finally installed ubuntu, and this time the double boot worked perfectly between ubuntu and win7.
Regarding the partitions, I've made:
- / root ubuntu installation: 20gb
- swap: 2gb
- /home partition: 60gb

and kept the old 100mb win7 file system and 30gb partition for win7
I'm glad that I've finally made it, thanks to you all.

---

