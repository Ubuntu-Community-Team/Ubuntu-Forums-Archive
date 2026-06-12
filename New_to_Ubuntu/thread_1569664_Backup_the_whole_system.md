---
title: "Backup the whole system"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by eithantlv on 2010-09-07
I have installed Ubuntu 10.04. Also I need to install some latest updates and some features. However, I want to backup the whole file system before I do this just in case that system crush(which just have happen before).
I have tried to use tar to backup my system and have not succeed("Exiting with failure status"). 
What is the best way for me to make such a backup?

---

### Post by lbrty on 2010-09-07
> **eithantlv said:**
> I have installed Ubuntu 10.04. Also I need to install some latest updates and some features. However, I want to backup the whole file system before I do this just in case that system crush(which just have happen before).
I have tried to use tar to backup my system and have not succeed("Exiting with failure status"). 
What is the best way for me to make such a backup?

Step-by-step instructions in the link below.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by HermanAB on 2010-09-07
Howdy,

I appreciate your concern.  However, provided that you make a separate partition for /home, all you really need to save is /etc, since it only takes about 30 minutes to re-install the system.  To preserve your data, do not format /home when you need to re-install.  You can then easily make backups of /home using rsync.

So, I usually just make a tar ball of /etc and leave it at that, since there is no point in backing up the whole Linux distribution that is available from multiple public servers.

---

### Post by mapes12 on 2010-09-07
Try

Remastersys
Clonezilla

Personally I use Remastersys.

As Herman AB comments it's all about having / and /home on their own partitions. The reason for this is that / has all your OS stuff and /home  has all your personal settings like what background and gnome desktop theme you have and also your FF bookmarks (but for the FF piece check out the FF addon Xmarks).

My machine only has Ubu installed and the partitions are formatted to ext3.

Partitions are:-
7GB = /
50GB = /home
2.5GB = Swap

Now, if i screw up my system I just reinstall Ubu making sure that at the partitioning stage of the install select "Advanced" and then manually tell the installer where to put "/" /home and Swap. Tell the installer to format the partition (7GB in my case) where "/" goes but DO NOT format /home (Otherwise your stuff and settings will be lost).

This gets me back up and running in no time. However, I then have to reinstall all my favourite application packages and Update Manager updates. So to cut this out I have Remastersys installed which I use periodically to make an installation .iso

If my system crashes I burn the Remastersys.iso to a DVD-RW (it's to big for a CD-R) and use this as the installation disk. This then reinstalls UBU "as before" i.e it includes all the apps and updates I had before the crash. Saves time and works a dream. When making the Remasters.iso I use the "dist" option. There are many HowTo's on the web for using Remasters.

For my stuff in /home I hook up an external HDD and use Grsync to backup everything in there. After the first backup the sync feature of Grsync only backs up new or changed files and so is very fast. I find I have to configure Grsync to --exclude=*/.gvfs in the Advanced tab as this hidden file causes me problems.

That's it. Nice n easy. Everything safe and sound. ):P

---

### Post by eithantlv on 2010-09-07
> **HermanAB said:**
> 
all you really need to save is /etc

But as I understand, that would not save some installed features (like skype, ICQ, PROXY-client etc.). I'd like to back them up too. Should I add any other directory to the archive then?
Thanks

---

### Post by Paddy Landau on 2010-09-07
I go an even easier way.

Back up your *entire disk* with [CloneZilla]("http://www.clonezilla.org/").

Then, if things turn out bad, simply restore the entire disk with CloneZilla. It will restore the entire disk exactly as you backed it up, undoing everything you did since then.

Alternatively, you can back up each partition separately -- especially when the computer holds both Windows and Linux, because you can restore just the partitions you need. That's what I do.

It works with Linux and with Windows (it has saved me many hours when my kids got viruses onto the Windows partitions, more than once!).

CloneZilla isn't the most user-friendly system, but it's easy once you've got your head around it. You'll need somewhere to store the backup. A subdirectory on an external hard drive will do fine.

---

### Post by Ruhani04 on 2010-11-04
Just another vote for clonezilla.
I don't know why but every so often my Ubuntu install just breaks as it did today. I haven't done any updates or changes but this morning gdm or the gnome desktop would no longer come to life. All I got was command line input.
Luckily I had backed up my whole disc as an image and with the help of clonezilla Maverick was back up and running within minutes.
I have been using Acronis True Image with Windowz and clonezilla works as well with Ubuntu.
8-)

---

