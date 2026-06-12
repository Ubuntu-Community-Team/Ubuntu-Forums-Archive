---
title: "Repartition and reinstallation questions"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Montblanc_Kupo on 2009-01-15
I recently installed lots of linux distros to test them out and eventually installed ubuntu as My primary OS... I've tweaked the hell out of it and probably not made the best partition scheme for it. What I'd like to do is save off My information and document etc., repartition the drive, install a clean copy with more space and and then put My files and such back.

My understanding is that I should be able to simply take My /home directory... throw it on an external drive or a dvdr or something... repartition (this time making a separate partition for the /home dir) and dump the old folder back and no harm no foul.

Is this the case? What should I look for as far as problems I might encounter? Any special procedures I would need to follow or special files and locations I'll need to grab? What about things like email and pidgin logs... are those in the /home dir as well?

---

### Post by earthpigg on 2009-01-15
if using the same version of the same distro, this is correct.

you will have to re-install software, but your old settings will be used when you do.

---

### Post by Montblanc_Kupo on 2009-01-16
Aww... weak... I finally have a thread I can thank in and the thank button is missing since the forum went down. :(

Oh well. Thanks! heh. 

Wow... linux is just sexy. hehe

---

### Post by Montblanc_Kupo on 2009-01-18
Okay... so there are a couple things I want to change for the sake of "Oh, I did that stupid at first and want to fix it but don't feel like losing all My data". ;)

* I want to have a separate /home partition.

* I want to ditch the /boot partition that I initially created because it doesn't seem like there is any point to it and it has caused problems in the past.

* I want to increase the size of My swap partition so I can actually use hibernate and standby without crashing (hopefully)

* I want to install fedora-core to test it on My machine since the Live CD doesn't have persistence. 

What I would like to do is have My partition scheme look like this:

-WinXp
-Unpartitioned Space
-Linux Distro
-Linux Distro
-Home
-Swap

Are there any problems with this setup? I realize I can't use the /home partition for more than one of the distros... but eventually it would just become the base home for whatever distro I end up sticking with... so right now Ubuntu's and fedora would just have it's own /home inside it's partition.

Are there any special concerns when setting up the boot structure since both Ubuntu and Fedora would both be on the system... My understanding is that one of them needs to be charge of the boot process... but I honestly don't understand it deeply enough to make sure it's all done correctly. I don't want to lose My winxp partition either since I need it for now so I don't want the MBR being broken by one of the installs.

---

### Post by albinootje on 2009-01-18
> **Montblanc_Kupo said:**
> I recently installed lots of linux distros to test them out and eventually installed ubuntu as My primary OS... I've tweaked the hell out of it and probably not made the best partition scheme for it. What I'd like to do is save off My information and document etc., repartition the drive, install a clean copy with more space and and then put My files and such back.


Why don't you make proper backups, and then use gparted to resize your partitions, and create new partitions ?

---

### Post by Montblanc_Kupo on 2009-01-18
> **albinootje said:**
> Why don't you make proper backups, and then use gparted to resize your partitions, and create new partitions ?

Well... that is the plan yes. So that's why I'm asking, what is the best way to accomplish this. I don't mind reinstalling software, I want to keep all My data... so My understanding was that simply copying the /home directory to an external device or another partition or drive would accomplish this.

Is there a more "proper" backup scheme you can suggest?

---

### Post by albinootje on 2009-01-18
> **Montblanc_Kupo said:**
> Well... that is the plan yes. So that's why I'm asking, what is the best way to accomplish this. I don't mind reinstalling software, I want to keep all My data... so My understanding was that simply copying the /home directory to an external device or another partition or drive would accomplish this.

From your original posting I understand that you want to backup /home and then do a clean reinstall.
But the tweaking that you've done might involve more than what is saved in /home ..
Hence my suggestion to do resizing (after making backups first, you don't want a power-failure destroying your data during a partition resizing..)
> 
Is there a more "proper" backup scheme you can suggest?
With proper backups I meant :
1) Back up everything you think you need to back up, that is /home
but perhaps also /etc and maybe more.
You know best what you have installed, but to give an example, let's assume you started using apache+php+mysql (from the Ubuntu repositories), then backing up /var/www and /var/lib/mysql too would make sense..
2) Make sure you back up to a "proper" filesystem in case you're backing up to some external device, or even archiving.
Copying files from Linux to a FAT32 partitions will end up with all your files and directories having the executable, which is not only ugly to work with, but also a potential security hazard because some files need to be 600 or 640.
If you have only FAT32 or NTFS on your external disk, then the best is the archive (tar.gz or zip) your /home.

---

### Post by Montblanc_Kupo on 2009-01-18
> From your original posting...

My original plan has changed since then, hence the later postings. The more I thought about it... the more I realized that I've messed with the install without knowing what I was doing (how else better to learn eh? ;) ) and have a couple issues that I can't solve and apparently no one else has any idea about either. hehe

So, I don't mind doing a fresh install... plus, I want to change the entire drive structure and install two different distros (ubuntu and fedora-core). I figured the best route was to just save My files... and nuke the rest. I'll have to reupdate, and reinstall software, and retweak My system... but I'll know I'm starting fresh and **hopefully** do things right this time. I haven't done much besides install software and updates. I'm just using this as a desktop computer. So I web surf... check email... use instant messenger... and play some games. Nothing that really requires serious consideration for backups. I wouldn't mind saving My pidgin chat logs... but other than that... I can't think of anything that is even saved on this machine besides some emerald themes and a highly tweaked compiz (which may or may not be part of the problems I'm having).

> Back up everything you think you need to back up, that is /home
but perhaps also /etc and maybe more.

I have no idea what is stored where really. It took Me a while just to figure out where My applications where installed... so I wouldn't know where to even start to think about looking for what to backup (again, that's part of the reason for this thread :) ).

> Make sure you back up to a "proper" filesystem in case you're backing up to some external device, or even archiving.

What I have right now is one large partition at the start of My hard drive with about 100GB for windows xp. Then a chunk of freespace. Then a bunch of linuxy stuff all on ext3. I created a 20GB partition at the beginning of the unpartitioned space using ext3 and I'm dumping stuff into that to hold things until I can sort out the end half of the drive (where linux and it's ... stuff... are located). Then I figured once I had the partition all sorted out, I would just plop the /home folder in as the root of the new /home partition. Is there any other trick to it? How do I make sure that My user accounts use the proper folders in the /home partition? I assumed that I just go into "users and groups" in the administration menu and point it at the /home folder I wanted for each user... anything else to it?

---

### Post by albinootje on 2009-01-18
> **Montblanc_Kupo said:**
> My original plan has changed since then, hence the later postings. 

OK :| :)
> 
Then I figured once I had the partition all sorted out, I would just plop the /home folder in as the root of the new /home partition. Is there any other trick to it? How do I make sure that My user accounts use the proper folders in the /home partition? I assumed that I just go into "users and groups" in the administration menu and point it at the /home folder I wanted for each user... anything else to it?

Hmmm, read this :
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by albinootje on 2009-01-18
Forgot to mention, if you're gonna have Ubuntu and Fedora and perhaps more Linux distributions which all are gonna use the /home partition, make sure that you are not using the same username and the same /home/your_username_here directory.
There's a chance that things can work out OK, but personally I would only try to "share" the Firefox and Thunderbird settings+data between those (and make regular backups).
Sharing the complete home directory for the same user(s) on two or more different Linux distributions with different application versions installed could lead to trouble.

---

### Post by Montblanc_Kupo on 2009-01-18
> **albinootje said:**
> if you're gonna have Ubuntu and Fedora and perhaps more Linux distributions which all are gonna use the /home partition, make sure that you are not using the same username and the same /home/your_username_here directory.

Yeah, kind of what I gathered. I had planned on setting it up and using it for Ubuntu and then if anything came long I finally decided to make the switch to, just set it up to use that instead... but only one at a time. I wanted to install fedora-core and I was just going to have it self contained (/home and boot from inside the same partition... shared swap which seemed to work out okay so far).

Is there anything special I need to know about multi-booting so that all three (or more) OS's show up correctly and I can choose them from the boot loader? I have been able to install linux mint and kubuntu without any issue while keeping My Ubuntu install as the primary os (and letting it deal with grub)... but since fedora-core is a different distro with a different base... it might do things differently?

---

### Post by albinootje on 2009-01-19
> **Montblanc_Kupo said:**
>  shared swap which seemed to work out okay so far).

Yes, swap partition sharing should be no problem
> 
Is there anything special I need to know about multi-booting so that all three (or more) OS's show up correctly and I can choose them from the boot loader? I have been able to install linux mint and kubuntu without any issue while keeping My Ubuntu install as the primary os (and letting it deal with grub)... but since fedora-core is a different distro with a different base... it might do things differently?

Well, Fedora also uses Grub. I guess it should be fine.

---

