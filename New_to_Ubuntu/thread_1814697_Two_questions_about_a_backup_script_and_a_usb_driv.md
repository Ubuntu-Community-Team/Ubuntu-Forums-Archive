---
title: "Two questions about a backup script and a usb drive."
date: 2011-07-29
forum: New to Ubuntu
---

### Post by eamonn on 2011-07-29
Hello,

I'm trying to work with the backup script that was provided at: [https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html) 

I do not have a CD-ROM drive and am trying to have the files backed up to my removable hard drive. 

I can find my hard disk at /media/TOSHIBA EXT but if I replace the line "dest="/mnt/backup"" with "dest="media/TOSHIBA EXT"" then I get the following error message:

> Backing up / to /media/TOSHIBA EXT/system-ThinkPad-X100e-Friday.tgz
Fri Jul 29 20:19:46 PDT 2011

tar: EXT/system-ThinkPad-X100e-Friday.tgz: Cannot stat: No such file or directory
tar: Removing leading `/' from member names
tar (child): /media/TOSHIBA: Cannot open: Permission denied
tar (child): Error is not recoverable: exiting now


And I'm a little unclear about how to move forward from here.

The usb drive is listed as "sdb1" in the "/dev" directory. If I replace the "dest=..." part of the script with "/dev/sbd1" I get the following error message:

> Backing up / to /media/TOSHIBA EXT/system-ThinkPad-X100e-Friday.tgz
Fri Jul 29 20:19:46 PDT 2011

tar: EXT/system-ThinkPad-X100e-Friday.tgz: Cannot stat: No such file or directory
tar: Removing leading `/' from member names
tar (child): /media/TOSHIBA: Cannot open: Permission denied
tar (child): Error is not recoverable: exiting now


In short, how do I backup to my removable hard drive? 

I also have a second, and not totally related to this post, question. I'm trying to become less dependent on the GUI and get more comfortable in the terminal. How would I view the files on the removable hard drive, located in /media/TOSHIBA EXT, through the terminal?

---

### Post by eamonn on 2011-07-29
Sorry, that script was found in the 8.04 documentation. 11.04 can be found here ([https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)) and it looks pretty similar.

---

### Post by Redblade20XX on 2011-07-30
It's been a while since I've done any scripting so forgive me if I may say something wrong. I think you'll need to get root privilege to write to the external usb so you'll need to include a command that will allow root privileges into the script. Idk the exact command but you can always google it. Hopefully this helps!! :)

---

### Post by eamonn on 2011-07-30
Thank you for helping. I still get this error message when I log in as root and run the script:
> tar: Removing leading `/' from member names
tar (child): /media/TOSHIBA%EXT/system-ThinkPad-X100e-Friday.tgz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now


---

### Post by fdrake on 2011-07-30
put double quotes (") around the path address"

"/media/../...Friday.tgz"

---

### Post by fdrake on 2011-07-30
> **Redblade20XX said:**
> It's been a while since I've done any scripting so forgive me if I may say something wrong. I think you'll need to get root privilege to write to the external usb so you'll need to include a command that will allow root privileges into the script. Idk the exact command but you can always google it. Hopefully this helps!! :)

what's the name of the formula on your avatar?

---

### Post by eamonn on 2011-07-30
I have double quotes around the "media/TOSHIBA EXT". Here's my edited version of the script:

> #!/bin/sh
####################################
#
# Backup script. This script is an edited version of a backup script found at [https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)
#
####################################

sudo

# What to backup. 
backup_files="/ /home /boot"

# Where to backup to.
dest="/media/TOSHIBA EXT"

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


---

### Post by Redblade20XX on 2011-07-30
> **eamonn said:**
> I have double quotes around the "media/TOSHIBA EXT". Here's my edited version of the script:

Just an observation between "TOSHIBA" and "EXT", is there a space because that usually causes a problem in linux.

---

### Post by Redblade20XX on 2011-07-30
> **fdrake said:**
> what's the name of the formula on your avatar?

It's Heisenberg's Uncertainty Principle from Quantum Mechanics! :)

---

### Post by eamonn on 2011-07-30
There is. What should I put between them?

---

### Post by fdrake on 2011-07-30
> # What to backup.
backup_files="/ /home /boot"
/home and /boot are mounted inside / so there is no need to back them up twice.

> # Backup the files using tar.
tar czf $dest/$archive_file $backup_files
still you have to use "" because your path name may contain spaces and special characters.
```
# Backup the files using tar.
tar czf "$dest/$archive_file" "$backup_files"
```

try and see if this works.

---

### Post by Redblade20XX on 2011-07-30
> **eamonn said:**
> There is. What should I put between them?

I think it's something like "TOSHIBA\ EXT". If I remember correctly.

---

### Post by eamonn on 2011-07-30
> **fdrake said:**
> /home and /boot are mounted inside / so there is no need to back them up twice.


still you have to use "" because your path name may contain spaces and special characters.
```
# Backup the files using tar.
tar czf "$dest/$archive_file" "$backup_files"
```

try and see if this works.

I want to say that it's working. A "system-ThinkPad-X100e-Friday.tgz" file has been created on my removable hard drive but, in the terminal, everything seems to be hanging around "tar: Removing leading `/' from member names".

It could also just be that everything is working and this is just taking a while because I'm backing everything up.

Thank you for helping.

---

