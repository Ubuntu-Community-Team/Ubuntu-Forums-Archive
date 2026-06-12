---
title: "I would like to create a disk image"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-01-06
I would like to make a backup of my Ubuntu partition (I'm duel booting). How can I create a disk image in case I toast this partition and want to reinstall Kubuntu with all my information and applications.

Thanks.

---

### Post by anystupidname1 on 2011-01-06
There are many ways, but Clonezilla is the first thing to come to mind and dd is the second.

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.linuxweblog.com/dd-image](http://www.linuxweblog.com/dd-image)

---

### Post by gmjs on 2011-01-06
Hi,

Yes--this one's a big question.  Also, since Ubuntu (and others) made ext4 the default file system during installation, it's knocked a few potentials off the list!

+1 for clonezilla though.  I've used the server version (DRBL) to perform a backup and restore and it worked very well.  Clonezilla Live supports the ext4 file system and can be installed and run from a USB pen.

The site states a limitation of only being able to restore from a single CD or DVD, rather than multiple ones--that's my only issue with the non-server version.

Hope this helps.

Graham

[COLOR="DimGray"]
(I've never used 'dd' to back up a partition.  I might have to try sometime!  It just copies (it stands for 'carbon copy' but 'cc' was already being used so they called it 'dd'--seriously!) the raw data from a device to a file.  I probably wouldn't recommend it if you're not completely happy at the command line, but you'd use a line similar to this to do it (probably using a live distro so that the partition is not mounted):

dd if=/dev/sda1 of=/backup/location/my-partition.img

if='input file' and of='output file')[/COLOR]

---

### Post by LewRockwellFAN on 2011-01-06
> **gmjs said:**
> 
The site states a limitation of only being able to restore from a single CD or DVD, rather than multiple ones--

Lest someone misunderstand this, may I elaborate a bit? Clonezilla itself fits just fine on one CD. But the image it makes doesn't have to be on a removable disk (CD or DVD or whatever) at all. You can keep an image of your Ubuntu boot partition on another partition of the same drive or on another drive. To me the sensible thing is to have a data partition and put it in a folder there named Partition_images or some such but you could have a separate partition for it or even put it on your Windows partition if you want. Of course if the image is small enough you can fit it on a CD or DVD. And remember the image doesn't have to be anywhere near as big as the partition being cloned. Clonezilla has several different compression modes and the highest compression mode is pretty darn efficient. Perhaps Clonezilla won't split it up automatically if it is too big for that (I don't recall ever trying) but that isn't much of a limitation. Just make the image on another partition of your hard drive and then use lxsplit or HJsplit or some such to split it down to CD size parts. But as a routine thing, unless you need the added physical security of being able to remove the media and store it remotely, or are really pressed to the wall on hard drive space, why bother? Restoring from a CD is a pain in the butt compared to doing it from a hard drive.

Clonezilla rocks! Ain't nothin like it. :)

---

### Post by sammiev on 2011-01-06
+1 for clonezilla and had tried a few restores with no problems well playing. Must others work good but clonezilla took the spot light for me. GL :)

---

### Post by steve7777777 on 2011-01-06
+1 for clonezilla. Last night I used it to replace a drive - SDA that was failing. The only unexpected thing about it is you have to specify the target prior to selecting the source. I use ext4 file system so this was one of the few options.

---

### Post by HermanAB on 2011-01-07
Howdy,

New Linux users always look around for a way to make a complete backup.  Old hands don't bother...

The reason is that Linux is very easy to install - much easier and faster than to recover a backup of the whole system, which can take hours to make and hours to restore.  Also, one day, when your disk dies, do you really want to re-install a 3 year old backup of a quaint old bug-ridden version of Linux, or would you want the latest version with the newest bells and whistles?

The trick is to install the system with a separate /home partition and make a backup of your data only, which is orders of magnitude less than the whole system.  Then, one day when the inevitable happens, you re-install Linux and make sure that your DON'T format /home and then you are back up and running in about 30 minutes.

---

### Post by Ghost_Mazal on 2011-01-07
+1 For imaging. Ubuntu is not so quick to re-install at all. It takes a long time to download and install all the extras you need to have a proper system. There is a lot of software and extras that doesn't come standard with ubuntu and it just takes much longer to download and install and config them again than simply restoring an image. It took me more than a week to get my installation working properly and have all the software you need. An image reload is an hour , done.

---

### Post by waynefoutz on 2011-01-07
Flyback is a good choice..it's modeled after Apple's "Time Machine."

[http://code.google.com/p/flyback/]("http://code.google.com/p/flyback/")

I find it just as easy to back up your /home folder on an external drive and reinstall. It only takes a few minutes to do it the old fashioned way.

---

### Post by waynefoutz on 2011-01-07
> **Ghost_Mazal said:**
> +1 For imaging. Ubuntu is not so quick to re-install at all. It takes a long time to download and install all the extras you need to have a proper system. There is a lot of software and extras that doesn't come standard with ubuntu and it just takes much longer to download and install and config them again than simply restoring an image. It took me more than a week to get my installation working properly and have all the software you need. An image reload is an hour , done.

This is why I use the "SuperOS" remix of Ubuntu. 

[http://hacktolive.org/wiki/Super_OS]("http://hacktolive.org/wiki/Super_OS")

All the extras are packed right into a DVD image. This DVD makes reinstalling Ubuntu a ten minute job.

---

### Post by gmjs on 2011-01-07
> **HermanAB said:**
> ...Linux is very easy to install - much easier and faster than to recover a backup of the whole system, which can take hours to make and hours to restore...you re-install Linux and make sure that your DON'T format /home and then you are back up and running in about 30 minutes.

Hmmm... that's true if you like all the defaults and install software only from the repository.  If you like to compile the odd application (for compatibility or to have the very latest version of a program) it can take a very long time to get everything set up again how you like it.

Reconfiguring a web server or updating the 'hosts' file--and anything else you've forgotten you did (and it does happen!) need replacing in the correct folders.

If you're a Gentoo Linux user, you'd definitely take an image backup of the operating system.  In Gentoo, you have to compile the whole system from the source code and it took my machine (Intel quad-core 4GB RAM) about 25 hours to compile X Server and the GNOME desktop.  Then everything else you want (perhaps Qt/OpenOffice.org/Scribus/GIMP) all need compiling too.  That's another few hours on top of that.  It literally takes about 2 days.  Images can be a very nice thing to have indeed.

On the other hand, sometimes it's nice to be forced into remembering how you did it the last time!

---

### Post by LewRockwellFAN on 2011-01-07
> **HermanAB said:**
>  ... one day when the inevitable happens, you re-install Linux and make sure that your DON'T format /home and then you are back up and running in about 30 minutes.

Perfectly true in outline, although for me, even though I am on DSL (and there may be some satellite or dialup users here), it is more like an hour and a half to do a fresh install. How much bandwidth you have might make a big difference here. Also where you are in the version maintenance cycle. If you are installing a version just released the day before there will be almost no updates to download. At the other extreme, if you are using a LTS version that is near the end of it's support phase there will be a LOT of stuff to download and it might take you half a day. Also depends on how much you tweak away from the defaults. If you customize much the clone approach works much better.

_**Restoring a clonezilla image from another hd takes me less than 5 minutes.**_ Of course, I keep only software on that partition, not data. I don't keep data in home, but if you want to you can put home on a different partition when you install to begin with. I find it more convenient just to keep stuff like custom icon images, desktop images, various config files and such in home.

---

### Post by skyzthelimit230 on 2011-01-09
Wow, thanks guys. Lots of information! :D

I think I'm just going to save the data I need and ythan reinstall if I toast the OS (which may happen). I'll use dropbox to back up all the files I need and let the rest go by the wayside.

---

