---
title: "can i create a restore point like windows"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-09
hey i've been away from linux for about a year (prison sucks) and have forgotten some stuff.  Is it possible to create a restore point before i update?  If so how?  and how do i do a restore if worst comes to worst?

---

### Post by psusi on 2010-03-09
No.

---

### Post by oldsoundguy on 2010-03-09
Actually, you can in a way if you create a separate partition for your ~/home folder.  Then all you need to is re-install. (or copy it to a thumb drive)

But court of last resort .. usually just using Grub at boot and running a repair or choosing an earlier kernel will do the deed if you kludged your install THAT BAD.  (only had to run the repair ONCE in 4 years)

---

### Post by MichealH on 2010-03-09
> **psusi said:**
> No.

Very well thought out answer there! :D

No you cant, Ubuntu Isnt Windows But you can backup your home directory And when you decompress it on a new install then you will have your ubuntu (Roughly how it was ) :)

Also Welcome to UF!

---

### Post by kanikilu on 2010-03-09
It's not as seemless, but if you have an another partition or hard drive (such as an external hard disk) to store backups, you could use something like Partimage from a live CD/USB to create an image of your computer.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

There are various ways to achieve the same result, this just happens to be one of them (e.g. good ol' dd, CloneZilla, etc.).

---

### Post by Mark Phelps on 2010-03-09
If you're running 9.10 and you installed it fresh (not an upgrade), you can't use Partimage because that can't handle Ext4 filesystems -- the default filesystem for 9.10.

Clonezilla can be downloaded, burned to CD, and then used to boot the machine and make full-partition backups to another drive.

So, you CAN use Clonezilla to make something much like a "restore point" -- with the exception that it will contain everything from the partition(s) you back up.  It can also later be used to restore the Ubuntu install from those backups.

---

### Post by oingk on 2010-03-09
OK clonezilla looks interesting.

In regards to the other thing you guys are saying about creating another partition for home folder, what exactly do you mean?

Basically is this a way to somehow save a backup of your system on this partition? So how can you save it (what program should you use) and then how can you retrieve it?

I am asking because I want to do something like this to keep safe from screw-ups.

---

### Post by psusi on 2010-03-09
You got me thinking and I've been doing some research.  It seems that the basic facilities to support something like this are in the works and I'm experimenting with them now.  I've installed 9.10 using LVM and once I got that done I created a snapshot, then rebooted and used the snapshot volume as the root.  This allows me to make modifications to the snapshot to test, and if things go wrong, I can just reboot from the original volume and all the changes will be ignored.  Right now I am upgrading to 10.04 alpha to see how that goes on the snapshot, then will try booting from the original volume to make sure I can switch between the two with ease.

In the future it should be possible to create the snapshot and tinker with the old system, then if things go all pear shaped, boot from the snapshot.  If you decide that things worked out, you can delete the snapshot, and if they don't, you can merge the snapshot back into the original root.  This merge support appears to be cutting edge still, and doesn't look like it will even make it in to 10.04.  Hopefully this will make it into 10.10 with a nifty gui and default configuration to use it in 11.04.

---

### Post by bradmayne04 on 2010-03-14
ok thanks!!! i appreciate all the feedback!!

---

### Post by quinnten83 on 2010-03-14
I think flyback kinda does what you want
[http://code.google.com/p/flyback/]("http://code.google.com/p/flyback/")

---

### Post by t.rei on 2010-03-14
Actually the way to keep your /home partition seperate is a really efficient thing to do to achieve a pretty huge amount of data security. With the horrid ease of installing a system nowadays thats mostly the fastest way to 'recover' data, too. :( I remember fixing things, because downloading it again was NOT an option. :D

small hint: remember the programs you frequently use and put a plain-text file in your home that says:
sudo apt-get install ubuntu-restricted-extras pidgin-otr yourapp1 yourapp2 ...

If you need to reinstall some day - just use that line to get it all back, fresh and new.

---

### Post by mike2357 on 2010-03-14
I have a script to run every day to backup files I need in case I accidentally trash something, which unfortunately I've done more than once.  I backup the following:

1.  /home (Users' personal files and settings)
2.  /etc  (System-wide configuration settings)
3.  /var/spool/cron/crontabs (Commands which run automatically)
4.  The script I wrote to generate the backup

There are some exceptions for files that take up a lot of space, but really aren't necessary, such as my browser's cached files.

The backup files are also handy when Ubuntu releases its next version.  I can do a clean install, and then recover the files I want, such as /home and some selected settings from /etc.

---

