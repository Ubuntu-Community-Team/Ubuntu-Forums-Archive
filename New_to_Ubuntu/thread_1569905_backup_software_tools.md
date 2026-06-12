---
title: "backup software tools"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by faial on 2010-09-07
Hi,
Which backup tool/SW should I use? I'm running JJ 9.04 and wish to backup all my system and personal info to an external HD once a week.
Thanks,
Orlando

---

### Post by sikander3786 on 2010-09-07
There are many options out there, what I use is Clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

Power tool also available on a live cd. Thats a + I believe.

Here is another link. Might help.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by mapes12 on 2010-09-07
Try

Remastersys
Clonezilla

Personally I use Remastersys.

It's all about having **/** and **/home** on their own partitions. The reason for this is that **/** has all your OS stuff and **/home** has all your personal settings like what background and gnome desktop theme you have and also your FF bookmarks (but for the FF piece check out the FF addon Xmarks).

My machine only has Ubu installed and the partitions are formatted to ext3.

Partitions are:-
7GB = /
50GB = /home
2.5GB = Swap

Now, if i screw up my system I just reinstall Ubu making sure that at the partitioning stage of the install select "Advanced" and then manually tell the installer where to put **"/"** **/home and Swap**. Tell the installer to format the partition (7GB in my case) where **"/" **goes but DO NOT format **/home** (Otherwise your stuff and settings will be lost).

This gets me back up and running in no time. However, I then have to reinstall all my favourite application packages and Update Manager updates. So to cut this out I have Remastersys installed which I use periodically to make an installation .iso

If my system crashes I burn the Remastersys.iso to a DVD-RW (it's to big for a CD-R) and use this as the installation disk. This then reinstalls UBU "as before" i.e it includes all the apps and updates I had before the crash. Saves time and works a dream. When making the Remasters.iso I use the "dist" option. There are many HowTo's on the web for using Remasters.

For my stuff in /home I hook up an external HDD and use Grsync to backup everything in there. After the first backup the sync feature of Grsync only backs up new or changed files and so is very fast. I find I have to configure Grsync to --exclude=*/.gvfs in the Advanced tab as this hidden file causes me problems.

That's it. Nice n easy. Everything safe and sound.

---

### Post by bodhi.zazen on 2010-09-07
There are many tools.

Personally I keep a separate /data partition and back it up with either tar or rsync.

See also : [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by lbrty on 2010-09-07
> **faial said:**
> Hi,
Which backup tool/SW should I use? I'm running JJ 9.04 and wish to backup all my system and personal info to an external HD once a week.
Thanks,
Orlando

I use FreeFileSync. In my opinion, I think it works the best and is the simplest to use.

[http://sourceforge.net/projects/freefilesync/](http://sourceforge.net/projects/freefilesync/)

---

### Post by cavh on 2010-09-07
I haven't used it, but have read good reports of Lucky Backup:

[http://luckybackup.sourceforge.net/]("http://luckybackup.sourceforge.net/")

---

### Post by HermanAB on 2010-09-07
Rsync is your friend...

New users always look for 'backup software' and always get disappointed to the point of laboriously writing their own.  Old hands use a one line rsync script.  If your rsync script is longer than 1 line, then you are doing it wrong.  The trick with rsync is not to specify what to backup, but rather specify wat *not* to backup.  The aim should be a zero maintenance one line script.

---

### Post by tahitiwibble on 2010-09-07
> **HermanAB said:**
> Rsync is your friend...

New users always look for 'backup software' and always get disappointed to the point of laboriously writing their own.  Old hands use a one line rsync script.  If your rsync script is longer than 1 line, then you are doing it wrong.  The trick with rsync is not to specify what to backup, but rather specify wat *not* to backup.  The aim should be a zero maintenance one line script.

Good morning,

Would you be so kind as to show us an example of your "one liner"? :)

---

### Post by Darkness Des on 2010-09-07
I entirely agree with the post above, Rsync is what should be used. I, actually, did make my own Backup script (GUI and everything), but Rsync should work for all people not willing to do this. Very easy to learn, there's even a GUI for it (grsync) that makes the process even simpler.

---

### Post by Arla on 2010-09-07
I like rdiff-backup for my data, I haven't actually bothered to backup my OS since I can reinstall that without too much difficulty.

---

### Post by keithpeter on 2010-09-08
Hello All

@tahitiwibble

```
rsync -avz --exclude=".*" /home/keith/ /media/Elements2/pundit-lucid-backup
```

If I added --delete to the options, I'd have a *synchronisation* rather than a backup. At present, if I delete something from the PC drive, then the file stays on the external hard drive. I don't back up dotfiles, but you can just leave out the --exclude=".*" if you do want to back up the dotties (configurations).

Its really important to make sure that the external hard drive is connected and working. One day, I'll do a bash script called backup that checks the drive is connected and writeable...

@everyone

I want to be able to image the whole hard drive of my T42 (dual boots XP with Ubuntu Studio) including the mbr so that if I foobar the installation I can just run a boot up cd, connect an external to find the image, and reinstall the lot. Like symantec ghost. Can clonezilla do that? If so, a set of idiot proof instructions would be welcome.

---

