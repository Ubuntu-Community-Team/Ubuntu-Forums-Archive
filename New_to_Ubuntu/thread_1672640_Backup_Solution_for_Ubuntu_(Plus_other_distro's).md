---
title: "Backup Solution for Ubuntu (Plus other distro's)"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by klossor on 2011-01-21
I'm looking for a backup solution for the latest linux build. Im running multiple machines so compatibility with not only ubuntu but multiple linux distro's would be ideal. (Crunchbang,Mint etc)

Also as there is a a lot of free space one these machines, I would like a program that only backs up actual files and ignores the free space.

For example on one machine I have a single hard drive, with 3 partitions on it. A 10gb primary partition for the /root, a 2 gb swap partition, and the remainder of the hdd space in a third partition containing /home. In total there is approximately 15gb's of data across all partitions, out of the total of 250gb on the hard drive. I would like a backup program that can take a snapshot so to speak of the device (/sda1) and save the partition configuration information and the data of 15gb.

Ultimately I would like to use a small external usb hard drive (320gb) to save several of these "images" in the event of a catastrophic failure. 

So is there such a program out there? Thanks in advance

---

### Post by howefield on 2011-01-21
Have a look at Clonezilla.

clonezilla.org

---

### Post by klossor on 2011-01-21
I took a look at clonezilla live version, the main problem I was having was that I could not set the target for the backup to a different device. 

I have tried several backup progs and the main problem im finding is setting the backup target directory to a usb hdd, any idea's?

---

### Post by howefield on 2011-01-21
There is a point in the "wizard" where you have to wait a few seconds for it to recognise USB devices, I think it states about 5 seconds, I usually give it at least 10 before moving on.

Never fails to pick up my Maxtor usb external.

---

### Post by klossor on 2011-01-21
Hmmm okay I'll give it a try, thanks for the help mate and the speedy responses ;)

---

### Post by HermanAB on 2011-01-21
Howdy,

New users always look around for a backup program.  Old hands know that it is mostly useless...

Use rsync to backup your data only, which should all be in your home directory.

Backing up the whole system is mostly a waste of time, since it takes much, much longer to restore a backup of an old tired version, than to do a fresh install of the latest and greatest Linux version.

If there was something that gave you a lot of trouble to install and configure, make a backup of the /etc directory for future reference, since all configuration settings are kept in there someplace.

---

### Post by klossor on 2011-01-21
> **HermanAB said:**
> Howdy,

New users always look around for a backup program.  Old hands know that it is mostly useless...

Use rsync to backup your data only, which should all be in your home directory.

Backing up the whole system is mostly a waste of time, since it takes much, much longer to restore a backup of an old tired version, than to do a fresh install of the latest and greatest Linux version.

If there was something that gave you a lot of trouble to install and configure, make a backup of the /etc directory for future reference, since all configuration settings are kept in there someplace.

Hmmm funny you should mention that, I thought to myself as I was planning what to backup that it seemed so counter-intuitive to backup actual programs and config settings as opposed to the data. I never would have dreamed of backing up anything other than docs/data while using windows in the past.

Mainly, as I imagine it is for most folks who are relatively new to Ubuntu/Linux, the reason I wanted a system wide backup was because I found a nice distribution and after quite some time setting up all the packages and configs I just wanted a clean image to reinstall should the worst happen. Most of the data on the machine will be sync'd to the cloud anyway so thats another reason I feel its more important for me to backup my actual system rather than the data on it.

I suppose if/when the worst happens I'll just have to bite the bullet and do a fresh install. Another option of course would be to create a custom install iso for the distribution, though I don't have much experience at all with creating custom distro's unfortunately.

---

### Post by kherring7383 on 2011-01-21
In the past I have personally used applications such as Acronis to make a complete clone of my Ubuntu drive and Grsync in Ubuntu to make backups of my Home Folder. However, Acronis is not a free utility and since the whole idea about FOSS is to find a free app to make backups.

Yesterday I came across an app called Redo backup and Recovery which is a Live CD from which you can boot. This CD is a complete OS with various applications to move files, access the internet and a host of other features. Now, I haven't actually made any backups, I have looked it over after burning the ISO and it looks promising. You may want to check it out.

---

### Post by Riffer on 2011-01-21
check out rsync.  There is a GUI for it.  I've tried it and it allows for you to backup any and all folders that you want and schedule it.  Having said that silly me never read the documentation so I ended up with huge back up files created once a week.

If I were you I would use rsync to backup just my data and go back and save my book marks and (if you use Evolution) my PIM/email data.

---

### Post by skypuppy on 2011-01-21
I'd like the complete backup capability to include mbr as needed, and everything so that if the disk dies, I can simply restore to the new disk and let-er-rip.  Then, I'll worry about updates and etc.  Incremental backups would then be nice, but always maintain the possibility of a complete disk failure recovery.

Does any software do this?
Thanks.

---

### Post by LexRoss on 2011-01-21
Hi,

I have tried many different backup tools including Partimage and now firmly believe that command line tools are best suited for automated backups. Rsync was too hard for me to master, so I am using BONTMIA script to do automatic backup of my system and home directory to an external USB hard drive. I just put a line in /etc/cron.daily/bontmia to make sure the drive is mounted before attemting a backup. I only back up /etc /usr/local and /home directories this way.

Shall you need a small disk image to be able to restore your system in case of catastrophic event, I would recommend FSArchiver which is also a command line tool. I used to use Partimage for doing this but FSArchiver is a new software and has several advantages over it including the ability to restore partition to the size smaller than original one, and can also back up several partitions into one image. Having said that, both are equally good. You just have to mount your network drive or whatever and you can keep an image of your system there.

---

### Post by HermanAB on 2011-01-21
If you want to rebuild your system the same way it was, then you should look at 'remastersys'.

On RPM distros, there is a utility called 'kickstart'.  Essentially, it is an automated install script.  There is a Kickstart for Ubuntu project, but it isn't done yet.  

Kickstart is the reason why RPM distros are popular in large institutions, since it makes replication onto diverse hardware incredibly easy.

---

### Post by bodhi.zazen on 2011-01-21
> **HermanAB said:**
> Howdy,

New users always look around for a backup program.  Old hands know that it is mostly useless...

Use rsync to backup your data only, which should all be in your home directory.

Well said.

Linux is not windows and it is rather trivial to re-install the OS.

You want to back up any user data (typically /home) as well as any system configuration files you customized (edited).

When I edit system files, I keep a copy of the original file and a copy of my edits  in /root/etc

To back up , tar or rsync /home and /root/etc. The only other backup you might need would be server side, ie database (mysql) or web pages (/var/www).

These backups are then much much smaller.

---

### Post by bodhi.zazen on 2011-01-21
> **HermanAB said:**
> If you want to rebuild your system the same way it was, then you should look at 'remastersys'.

On RPM distros, there is a utility called 'kickstart'.  Essentially, it is an automated install script.  There is a Kickstart for Ubuntu project, but it isn't done yet.  

Kickstart is the reason why RPM distros are popular in large institutions, since it makes replication onto diverse hardware incredibly easy.

Kickstart is nice, you can do a similar thing with apt though.

Many methods to do this, basically dpkg --get-selections

One (of many) seamples:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

---

### Post by klossor on 2011-01-21
Thanks for all the replies guys, it looks like I've got some nice options, and some reading to do ;) It's much appreciated all.

@LexRoss

Thanks man, I'll have a gander at a BONTMIA script, and FSArchiver :p

@HermanAB

Cheers for the responses so far mate, I'll have a look into kickstart and keep an eye out for an ubuntu version. Still right now it could help me out with other machines i've got.

@bodhi.zazzen

If I go ahead and Tar or rsync the /home, will the backup include the free space? or will it simply take the data contents? Also thanks for the cloning install link man


Klossor

---

### Post by Megaptera on 2011-01-21
Here's more about Remastersys mentioned above:
" Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it."

I've found it really useful and easy to use.
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by klossor on 2011-01-21
> **Megaptera said:**
> Here's more about Remastersys mentioned above:
" Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it."

I've found it really useful and easy to use.
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Hey nice one man, option 2 seems to be just what im looking for, I'll drop over and give her a run through, appreciate the heads up ;)

---

### Post by Megaptera on 2011-01-21
You're welcome!

---

### Post by bodhi.zazen on 2011-01-21
> **klossor said:**
> @bodhi.zazzen

If I go ahead and Tar or rsync the /home, will the backup include the free space? or will it simply take the data contents? Also thanks for the cloning install link man


Klossor

tar and rsync will back up data only, not free space.

rsync will make a baseline, and subsequent backups will only backup files that have changed.

---

