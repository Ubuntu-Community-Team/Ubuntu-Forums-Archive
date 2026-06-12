---
title: "Looking for a good and simple backup software"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Bjornar93 on 2010-12-27
Hi!
I have been looking for hours after a good backup software that applies to me.
I have a 320 GB harddrive in my laptop, and I have bought a 320 GB externable harddrive. The harddrive in my laptop is divided into three partitions. A ext4 for Ubuntu, a NTFS partition Windows 7 and another NTFS partition for my personal files. What I want is a automated backup every month of all the partitions in my laptop to the externable drive. Every change on the laptop harddrive would then be transferred to the externable monthly. Like if I delete a file on the laptop, then it would be deleted on the externable too. I do not want the backup to be saved as a big file that I need software to restore the files from. I want the backup to be saved in folders, just like on my partitions. If this question has been asked before, then I'm sorry, but I am so tired of looking after a good program that applies too me, so I just had to ask :roll:

---

### Post by HermanAB on 2010-12-27
Howdy,

Making backups on Linux is exceedingly simple.  That is why you cannot find anything.  A good rsync backup script is a one liner.

However, there are several incredibly complex backup solutions available.  Most of them are fancy GUIs with rsync hidden deep down underneath all the glitz.  No matter how simple a tool one makes, someone else will always find a way to make it more difficult to use.

So, you have a choice, read the rsync man page, or install Bacula, Dervish, Rbackup, Amanda or Zmanda.

Pick your poison.

---

### Post by Bjornar93 on 2010-12-27
HermanAB: Thanks for your answer!
Will have a look at those tools you mentioned! :)

---

### Post by seawolf167 on 2010-12-27
For a good GUI backup I prefer sbackup

```
sudo apt-get install sbackup
```

You can include/exclude what you like (as you advance), and it stores its backups incrementally & in tar files.[URL="http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html"]

Tutorial[/URL]

---

### Post by stmiller on 2010-12-27
This will copy all files and folders recursively, including hidden files:

```
rsync -a /home/you /destination/harddrive/
```

There is also grsync:

[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)

---

### Post by donkyhotay on 2010-12-27
Personally I just copy/paste my folders over. It works if you want something easy to do with no setup. Course it's harder in the long run since you're doing everything manually so not really recommended.

---

### Post by sammiev on 2010-12-27
I'm using a USB HD for backups and I really like Clonezilla as it also backs up any and all OS on the HD. GL :)

---

### Post by seawolf167 on 2010-12-27
> **stmiller said:**
> This will copy all files and folders recursively, including hidden files:

```
rsync -a /home/you /destination/harddrive/
```

Add in a --delete to delete extraneous folders/files and that looks good

```
rsync -a --delete /directory/to/backup /place/to/save/backup
```Or you can use tar

```
tar -cvpzf backup-name.tar.gz --exclude=/path/to/exclude /directory/to/backup
```

---

### Post by Bjornar93 on 2010-12-27
seawolf167: Seems like a good program :)

stmiller: Interesting! :)

donkyhotay: Well, that works, but it would be great with a program to backup for me ;)

sammiev: Clonezilla sounds good, will take a look :)

---

### Post by oldfred on 2010-12-27
I saved these links and use the bash script which is really the one line rsync mentioned above. I only backup my data as I presume I will reinstall the system but save all of /home (user settings) as my data is all in another partition. I also backup any files I manually maintain in /etc (system files) by copying them into a folder in /data. I also include in my script an export of a list of all installed apps so I can easily reinstall everything. So my backup is several things. While the rsync is easy I do not consider it the full backup as only the copies to DVD save the version I deleted but did not mean to delete.:)

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Quote:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh
additional parameters:
-l: copies symlinks as symlinks
-t: preserves modification times
-D: preserves device and special files


```
#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

#rsync -auvP /home /media/backup
#rsync -auvP /share /media/backup
#rsync -auvP /media/floppy /media/backup
#rsync -auvP /etc /media/backup
echo "done"
exit 0

```
make it executable
chmod +x mybackup.sh

run it
./mybackup.sh

of course, do the dry run first as I said before
thank you very much. I made a symbolic link from /bin/backup to /root/backup.sh, thanks!!!!!

---

### Post by Bjornar93 on 2010-12-27
oldfred: Thanks for your answer! :)

---

