---
title: "best method of backing up home folder"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-06-05
Hi
I have a home folder with 2.3 gig of data
I am keen to back it up before updating my system
What I was going to do is create a .tar archive file and then save this
Is this the best/ easiest method?
Thanks

---

### Post by DBrocks on 2009-06-05
A .tar.gz archive will offer you some compression, but will take longer to compress/decompress. What media are you backing it up to? Another HDD, another partition, CD, USB?
Also: you can update your distro without backing up. [http://www.howtoforge.com/how-to-upgrade-ubuntu-8.10-to-ubuntu-9.04-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.10-to-ubuntu-9.04-desktop-and-server) Is a good tutorial on upgrading your system version. I upgraded my server from 8.10 to 9.04 a few weeks ago, which was nerve-racking, but now I'm sitting pretty on Jauty SE. Though backing up is not entirely necessary, its not a horrible idea.

---

### Post by tiyowan on 2009-06-05
Hi there,

It's the easiest method, yes. :)

However, if you ever decide to learn some shell scripting in the future, then you could also write a script that automatically backs up your home folder.

Cheers.

---

### Post by Sir Jasper on 2009-06-05
Hi again Duke,

I cannot say what is the best method; however I use "sbackup" to back up to one of my faster USB sticks.

It runs in the background and you can check if its finished with top or htop.

With 2.3 GB it MAY take perhaps 20 minutes to an hour or so.

I always delete my old backup first as I don't bother with the incremental option.

If you decide to use it and if you have any problem just ask.

My regards

Addendum:

Sbackup also records some additional settings. I actually use it every day or two using alternate USB sticks.

I also clone everything (every 10 days, just in case) to an external hard drive but as I use a paid program I'll leave others to advise a good free method.

---

### Post by eMJayy on 2009-06-05
I came across a similar question a little while ago. 

[http://ubuntuforums.org/showthread.php?p=7404652#post7404652](http://ubuntuforums.org/showthread.php?p=7404652#post7404652)

Creating a tar.gz of the files you want to back up in your home directory is definitely the easiest method. I have 3 hard drives, so I tend to store the majority of media files on the secondary drives. I basically do this because I dual boot Ubuntu and Windows. The harder option is to create additional partitions to store stuff.

---

### Post by tea for one on 2009-06-05
> **Duke Togo said:**
> Hi
I have a home folder with 2.3 gig of data
I am keen to back it up before updating my system
What I was going to do is create a .tar archive file and then save this
Is this the best/ easiest method?
Thanks

Good evening

It may be worth considering Grsync available via synaptic.

Here is the website for further information:- [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by nothingspecial on 2009-06-05
> **DBrocks said:**
>  Though backing up is not entirely necessary, its not a horrible idea.

Backing up is always necessary. Believe me I know.

---

### Post by GMachine_24 on 2009-06-05
I would just like to echo nothingspecial's advice on backing up:

Do it now; do it often. Never attempt a version upgrade of your computer without backing up your data files. Ever.

You can back up various ways, using tar, rsync (which I use to keep two hard drives synchronized, one as a back up).

Anyway, I just wanted to say YES back up. Always.

--gm

---

### Post by abhiroopb on 2009-06-05
I provide a guide on my blog on how to use rsync to backup. Have a look...I use a cron job to have it run once every 3 hours, and it always backs things up.

Also since its only 2.3GB, I'd suggest using dropbox as well (have a look at my signature).

Here's my blog posting: [http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html)

---

### Post by LewRockwell on 2009-06-05
I use Clonezilla to clone disks and partitions

---

### Post by Polaris96 on 2009-06-05
I'd worry about archiving if I had statistical data I'd be keeping for legal purposes (like biz emails, etc).  Why .tar something if you'll want to check it out later?  Tarballs are better for mailing stuff, these days.  Archives are usually unnecessary with modern mass storage.  

So far as specialized backup protocols go, they're awesome, but you're only talking about backing up data - not systems which must be able to function in a topology different from the one they were created in.

It's the /home folder, for pity's sake, and removable media is big now.  If you have a DVD burner, I'd just take a periodic burn onto DVDRs with no compression or archiving.  It's what I do, BTW.  I rewrite a DVDRW weekly and, Monthly, I burn a DVDR with the last week's /home.  After a year I start chucking the old discs.  

If I travel, I just grab the DVD and take /home with me! You have to remember to resync any files you alter in that case.  I save 'em to a USB stick and dump 'em back on my HDD when I'm home.  

Simple, cheap, portable, and, if you go Dual Layer, you can get almost 10G on a single disk.

---

### Post by rplantz on 2009-06-06
I have posted the rsync script I use for snapshot backups at [http://ubuntuforums.org/showthread.php?t=1180122](http://ubuntuforums.org/showthread.php?t=1180122)

---

### Post by mikechant on 2009-06-08
> It's the /home folder, for pity's sake, and removable media is big now. If you have a DVD burner, I'd just take a periodic burn onto DVDRs with no compression or archiving.

I'd also add that even in cases where compression would be useful (e.g. you've got 5Gb of data and you'd like to fit it on one 4.7Gb DVD), it's still usually pointless to even try since most large data files which make up the bulk of most peoples' data are already highly compressed with efficient data-type specific algorithms - e.g. most audio, video and picture files. These sort of files can even get slightly bigger when 'compressed' for a second time!

---

