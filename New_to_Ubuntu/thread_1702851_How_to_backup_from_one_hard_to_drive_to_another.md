---
title: "How to backup from one hard to drive to another?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by 007casper on 2011-03-08
I am trying to figure out how to take a snapshot of my hard drive.  
The drive I want to back up doesnt have any system files. It only has my data, which is around 890GB and want to copy it to another drive as a backup.  I have always "copy and paste" files from one drive to another.  When the data drive becomes 890GB, this process becomes not efficient at all.

Once all the questions are answered,  I am going to edit this original post here, so veryone can use it as a guide.

I found this link in regarding to making a backup through shellscripts.  
[https://help.ubuntu.com/10.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/10.04/serverguide/C/backup-shellscripts.html)

The script shows how to back up certain directories in your system drive.  However, in my set up, I have three hard drives connected to the computer. The first one is the system drive, the other is the data drive, and the third harddrive is the backup of the "data drive".

I just want to make sure I revised the script properly.  Please, advise.  Thank you.

The following shell script uses tar to create an archive file. 
```

#!/bin/sh
####################################
#
# Backup to NFS mount script.
#
####################################

# What to backup. 
backup_files="/media/data1"

# Where to backup to.
dest="/media/backup1"

# Create archive filename.
day=$(date +%A)
hostname=$(hostname -s)
archive_file="$hostname-$day.tgz"

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files

# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest

```  

The simplest way of executing the above backup script is to copy and paste the contents into a file. backup.sh for example. Then from a terminal prompt: 
```

sudo bash backup.sh

```

To see a listing of the archive contents. From a terminal prompt:
```

tar -tzvf /mnt/backup1/host-day.tgz

```

---

### Post by cjhabs on 2011-03-08
If you use tar then all your files from the source drive will be bundled into a single file on the destination, and you will need to "untar" to get to the contents.

I personally use rsync - which is particularly effective on subsequent backup passes when it only backs up the changes.

I use:
rsync -au --exclude='.cache' --exclude='.recoll' --exclude='Downloads' --exclude='vm' /path_of/source/ "/media/backup_drive/Data/"

you can exclude as many folders from the source as you desire (or none) - your folder names will obviously vary - the first the source, the second is the destination.

I don;t recall if rsync was loaded by default or needed to be added from the repositories.

be careful of the trailing slashes - that controls where files get placed - I suggest running a small test on a sub-folder before kicking off the full backup.

---

### Post by vanadium on 2011-03-08
Essentially, a mirror copy of a data directory to another destination boils down to
```

rsync -av --delete <source> <target>

```
This will make a copy preserving all file attributes from the original. Only changed files are copied, so a subsequent run will be lightning fast. Files that have been deleted in the source will also be deleted in the target.

You can indeed add other options such as --exclude to exclude some files.

You would use -u if you are not very consistent and edit files both on the source and destination. However, then you certainly do not want to use the --delete option. And in order to have most recent versions on both source and destination, you would run rsync in both directions. Clutter, i.e. files that you deleted in either source or destination, would accumulate, though. For such a scenario, unison would be more appropriate.

---

### Post by danjahner on 2011-03-08
If you are looking for a mirror backup of the data drive, have you thought about setting up RAID1 and not having to worry about a script?

---

### Post by 007casper on 2011-03-08
I did a test with cjhabs example. It works really nice, and dont have to wait files to copy

I am going to give it a shot to what vanadium suggested

regarding raid1.  I was one of the early adaptors in PC.  I have never had a good experience.  I really tossed the whole raid idea when the raid when out of sync in PC a few years back, and corrupted a lot of my data.  I was never able to retrieve back my data the way you would hope. 

Maybe raid is solid now.  However, a few bad experiences, plus performance issues makes me not go back to it.  There is nothing wrong with script, and you can even cron it.  I really think it will be more reliable than raid.  It will be fast too.  I dont have to worry about performance issues.

any other suggestions welcome...

---

