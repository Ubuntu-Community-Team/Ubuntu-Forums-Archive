---
title: "Backup"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-08-28
Is there a backup software that will allow me to save my settings of all the applications I've installed?

Is it possible with sbackup or rsync?

Thanks

---

### Post by Amida on 2010-08-28
I am not sure is this suits your needs but you can try "Back In Time" 

```
sudo apt-get backintime-gnome
``` or
```
sudo apt-get backintime-kde4
```

More info here: [http://backintime.le-web.org/](http://backintime.le-web.org/)

I haven't tried it yet but I think that you can backup the folders, containing your configuration files.

Cheers, hope this helps :)

P.S.: your Avatar is really cool =D>

---

### Post by XubuRoxMySox on 2010-08-28
It's called [Remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")! Google Ubuntu Remastersys for some easy tutorials and stuff. It makes a LiveCD of your just-the-way-you-want-it system, software and all!

-Robin

---

### Post by jakupl on 2010-08-28
As usual on Ubuntu Forums, you get 10000 different answers, but in your case, I would back up to an external hard disk using tar.

go to terminal and do something like:
```
tar -pczvf /path/to/backup/destination.tar.gz /home/username
```

and to recover:

```
tar -xzvf /path/to/backup/destination.tar.gz
```

I haven't tried it, but it should do the trick. I don't think you would need super user privileges.

This will not backup programs, only the program settings. So you will have to install the programs again, but once you have installed them, the settings will be the same. Thisway you avoid having to backup Gigabytes of excess data.

---

### Post by mapes12 on 2010-08-28
It's all about having **/** and **/home** on their own partitions. The reason for this is that **/** has all your OS stuff and **/home** has all your personal settings like what background and gnome desktop theme you have and also your FF bookmarks (but for the FF piece check out the FF addon Xmarks).

I've attached a screenshot to show how I divide up my HDD. This machine only has Ubu installed and the partitions are formatted to ext3.

Partitions are:-
7GB = /
50GB = /home
2.5GB = Swap

Now, if i screw up my system I just reinstall Ubu making sure that at the partitioning stage of the install select "Advanced" and then manually tell the installer where to put **"/" /home and Swap**. Tell the installer to format the partition (7GB in my case) where **"/"** goes but DO NOT format **/home** (Otherwise your stuff and settings will be lost).

This gets me back up and running in no time. However, I then have to reinstall all my favourite application packages and Update Manager updates. So to cut this out I have Remastersys installed which I use periodically to make an installation .iso

If my system crashes I burn the Remastersys.iso to a DVD-RW (it's to big for a CD-R) and use this as the installation disk. This then reinstalls UBU "as before" i.e it includes all the apps and updates I had before the crash. Saves time and works a dream. When making the Remasters.iso I use the "dist" option. There are many HowTo's on the web for using Remasters.

For my stuff in **/home** I hook up an external HDD and use Grsync to backup everything in there. After the first backup the sync feature of Grsync only backs up new or changed files and so is very fast. I find I have to configure Grsync to **--exclude=*/.gvfs** in the Advanced tab as this hidden file causes me problems.

That's it. Nice n easy. Everything safe and sound.

---

### Post by drascus on 2010-08-28
> It's called Remastersys! Google Ubuntu Remastersys for some easy tutorials and stuff. It makes a LiveCD of your just-the-way-you-want-it system, software and all!

Thanks that's the tool I have been looking for, for a while...

---

### Post by Fifthmarch on 2010-08-29
Thanks for the nice words about my avatar, Amida. Of these options, Remastersys seems to be the one most suited to my needs (I'm a novice, so copying the config files, and then updating them in the new OS is a little confusing.)

I've got the .iso file done using Remastersys, and I'm trying it out on a virtual machine. But it's just showing a single word "Loading...." Has this happened to anyone?

---

### Post by diacad on 2010-08-29
I am also looking for a way to back up an Ubuntu 10.4 installation.  But how can this "Remastersys" back everything up on a CD or DVD?  They only hold a few Gb at most.  And hard disks in most machines are 40 Gb or much larger.  Does it use multiple DVDs in this case?  This would mean dozens, in many cases, particularly if your disk is full. It would be much better to back up to am external USB drive, since terabyte drives are now available for $100 or so, and will store more than 200 DVDs worth of data.  If "Remastersys" can use an external USB drive as a target for both backup and restore, I would be interested.  Another point - does the target system for restore have to be a similar machine?  This could be a problem if the original hardware failed or was destroyed in a fire.

---

### Post by ezsit on 2010-08-29
> But how can this "Remastersys" back everything up on a CD or DVD? They only hold a few Gb at most. And hard disks in most machines are 40 Gb or much larger. Does it use multiple DVDs in this case? This would mean dozens, in many cases, particularly if your disk is full.

You are not thinking of remastersys the right way. Backup your data separately. Backup your pictures, your music, your files, etc to an external hard drive and leave your /home folder with just the settings and no other personal data. Leave your /home folder empty of all personal files. Make sure to leave all the standard folders in your /home folder, such as Pictures, Documents, Music, Public, etc - just leave them empty!. Then run remastersys in backup mode. This should create a backup ISO that can easily fit on one DVD. When you restore, copy your data back after you restore your system. Backups should always keep system and personal data separate.

PS. The more stuff you leave in your /home folder, the more space your system backup will require and the more memory your backup will require to boot. Everything in /home gets loaded into RAM, so leave your /home folder as empty as possible. **Leave all the .files and .folders.**

---

### Post by inameiname on 2010-08-29
Indeed. Remastersys is the best way to go. 

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Personally, I just back up all my 'My Documents' onto recordables/flash drives and then once I've tweaked it all to my liking, I just make a full backup of my computer using Remastersys. It compresses, and can go a maximum of 4.4 GB for an ISO which will essentially work just as the Live CD you first install from Ubuntu on their website, but with all of your tweaks and settings.

Simple, simple. :)

---

### Post by mikodo on 2010-08-30
> **mapes12 said:**
> It's all about having **/** and **/home** on their own partitions. The reason for this is that **/** has all your OS stuff and **/home** has all your personal settings like what background and gnome desktop theme you have and also your FF bookmarks (but for the FF piece check out the FF addon Xmarks).

I've attached a screenshot to show how I divide up my HDD. This machine only has Ubu installed and the partitions are formatted to ext3.

Partitions are:-
7GB = /
50GB = /home
2.5GB = Swap

Now, if i screw up my system I just reinstall Ubu making sure that at the partitioning stage of the install select "Advanced" and then manually tell the installer where to put **"/" /home and Swap**. Tell the installer to format the partition (7GB in my case) where **"/"** goes but DO NOT format **/home** (Otherwise your stuff and settings will be lost).

This gets me back up and running in no time. However, I then have to reinstall all my favourite application packages and Update Manager updates. So to cut this out I have Remastersys installed which I use periodically to make an installation .iso

If my system crashes I burn the Remastersys.iso to a DVD-RW (it's to big for a CD-R) and use this as the installation disk. This then reinstalls UBU "as before" i.e it includes all the apps and updates I had before the crash. Saves time and works a dream. When making the Remasters.iso I use the "dist" option. There are many HowTo's on the web for using Remasters.

For my stuff in **/home** I hook up an external HDD and use Grsync to backup everything in there. After the first backup the sync feature of Grsync only backs up new or changed files and so is very fast. I find I have to configure Grsync to **--exclude=*/.gvfs** in the Advanced tab as this hidden file causes me problems.

That's it. Nice n easy. Everything safe and sound.

I need clarification of this process, please. Would this be the process?

1. Use the current Ubuntu Live CD to reinstall, with manually installing /home partition from before.

2. Burn the iso. of Remastersys to DVD, from where it is saved.

3 .**Reinstall  the OS, with the Remastersys DVD.**

4. Bring your data from backup into /home.

Is that it?

Thanks.

---

### Post by diacad on 2010-08-30
ezsit: I see what you mean.  I was looking for something like Norton Ghost.  Remastersys sounds like a way to create only a system recovery disk, not a full backup solution (with data and programs as well).  A guru friend who uses it has recommended Partedmagic, a collection of tools that can be downloaded (free) from partedmagic.com.  Anyone had experience with this?  Much of it is over my head (this is an "absolute beginner" thread), but one of the tools, Clonezilla, seems more what I am looking for from the description.

---

### Post by inameiname on 2010-08-30
When I used Windows, Norton Ghost was my baby, and when I switched to Ubuntu, I looked all over trying to figure out a Ghost equivalent. My favorite ended up being Remastesrys, despite not really being like Ghost, as in it doesn't make an image exactly, or in the same way. But it does perform a full backup, of every single thing as it is exactly if you desire with about 2 clicks. And more. The ability to run as a live cd is really helpful for me. 

Also, here is a good link to a poll done recently about favorite backup tools:

[http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html](http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html)

---

### Post by ezsit on 2010-08-30
> Remastersys sounds like a way to create only a system recovery disk, not a full backup solution (with data and programs as well).

I relied on Ghost for years when using Windows. Towards the end of my Windows usage, I switched over to storing my documents and other data on removable hard drives and reinstalling Windows when needed. I guess I broke my dependence on Ghost that way.

Remastersys can do full backups, just limited to 4.4GB total filesize. 

If you store your data separately, Remastersys works wonderfully in DIST mode to save your system and all installed apps. It really is a very reliable and simple method.

If you start imaging partitions, then you'll need to start editing grub files and become proficient at manipulating UUIDs. Remastersys makes reinstalling a breeze.

---

### Post by candtalan on 2010-08-31
I looked at remastersys however I saw that it was commented as 'unverified' software. I guess that means that it is not in the ubuntu repositories or something?
I did not proceed, because I woul dreally prefer to aviod unverified sw.

---

### Post by -kg- on 2010-08-31
If you're looking for a substitute for Norton Ghost, you might want to check out [Clonezilla Live]("http://clonezilla.org/").

I have Clonzilla Live on a USB Flash drive, and it works pretty well like Norton Ghost in backing up partitions (and whole hard drives, if you want).  I made an image of my root partition today, and it seems to have done a thorough job.  I haven't tried to reinstall, but Clonezilla has been around for quite a while, and I assume that it works as advertised.

Check it out...it may be what you're looking for.

---

### Post by Fifthmarch on 2010-08-31
> **ezsit said:**
> 

PS. The more stuff you leave in your /home folder, the more space your system backup will require and the more memory your backup will require to boot. Everything in /home gets loaded into RAM, so leave your /home folder as empty as possible. **Leave all the .files and .folders.**

Actually, remastersys installs along with a GUI. There's an option there to leave out all your personal files. I think using that would be simpler than deleting files for backup. 

Does anyone have an idea as to why I can't run the remastersys image on a virtual machine?

---

### Post by indytim on 2010-08-31
For a complete H/D backup solution, I would recommend fsarchiver
[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

It will do a partition level backup.  Covers all of your partitions including
ntfs,
fat32,
ext3,
ext4

I use it in combination with RescueCD [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") on a weekly basis backup rotation (23 partitions).

Remember Remastersys is limited to your ops.  No help on your data partition(s).

-DataMan

---

### Post by inameiname on 2010-08-31
Remastersys isn't available in the repos, but has it's own via that link I gave above. It's only considered 'unverified' because it doesn't include a pubkey that is accepted by Ubuntu. Whatever. Doesn't mean it's a bad thing. Remastersys is great. Plus, the creator is such a nice gent in helping with all sorts of problems. Never gotten that much help from those that make the thing like it. Saved me once or twice with his suggestions. Hehe

---

### Post by Fifthmarch on 2010-09-05
Just a note - 

I found out why my remastersys dvd didn't work - it was because there was not enough space in my /home folder to complete the iso.

When I tweaked the settings so that the remastersys folder was created on another partition, I got a working DVD.

---

