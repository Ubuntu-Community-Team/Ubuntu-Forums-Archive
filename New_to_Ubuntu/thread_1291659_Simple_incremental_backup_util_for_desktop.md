---
title: "Simple incremental backup util for desktop"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Razmear on 2009-10-14
I took a look at BackupPC before posting this, and it wants to install apache and a bunch of other stuff I don't need, which is why I'm asking this question. 
I just had one HD crash and want to be prepared for when the next one dies. 

I'll be backing up to an 8gig USB stick and just need to grab the contents of my home folder. I need to be able to exclude directories (Regnum Online for one, as it's a huge game and installs to my home directory for some lame reason), and would like to get incremental snap shots about once a week to keep my mail stores recoverable. 

Right now I'm doing a simple copy to USB of the home folder just to be safe, but I'd like a bit more sophisticated method, preferably with a graphical interface. 

Any suggestions to keep me from trying out a few dozen programs before finding the best one out there for my needs? 

Thanks,
eb

---

### Post by winotree on 2009-10-15
**grsync** should be in the repositories --  it does a fine job of incremental back-ups on my /home file.  Here, [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/) take a look at it.  :)

EDIT -- misread your post so edited my comment for clarity [you're not trying to back-up an 8GB stick but back-up **to** an 8GB stick].

---

### Post by Razmear on 2009-10-15
> **winotree said:**
> **grsync** should be in the repositories --  it does a fine job of incremental back-ups on my /home file.  Here, [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/) take a look at it.  :)



Thanks, installed it and will give it a try when my original 2.5gig file transfer finishes up. 

A semi-related n00b question:
If I simply copy my home directory into a new install of Ubuntu will my login automatically show on startup and password work or do I need to do any additional tweaking to get back up and running? 

Thanks for the first tip!
eb

---

### Post by jpkotta on 2009-10-15
> **Razmear said:**
> Thanks, installed it and will give it a try when my original 2.5gig file transfer finishes up. 

A semi-related n00b question:
If I simply copy my home directory into a new install of Ubuntu will my login automatically show on startup and password work or do I need to do any additional tweaking to get back up and running? 

Thanks for the first tip!
eb

No, your password, UID, etc. are associated with the system, not your home.  You need to make a user on the new install, and then chown your copied home so that the new user can access it.  If the new user has the same UID* as the old, you probably just need to move the old home directory.

```

# Assume new user has been created, and we don't care about the $HOME that was created for new user.
sudo mv old_home/ /home/*username*
sudo chown -R *username:username* /home/*username*

```

*The UID is the number that the OS knows the user by.  Usually it is 1000 (or 1001, 1002, ...) on Ubuntu.

---

### Post by Razmear on 2009-10-15
The backup just completed with errors... 

```

rsync: mkstemp "/media/KINGSTON/grsync/.evolution/mail/views/.current_wide_view-mbox:_home_eb235_.evolution_mail_local_Inbox.xml.T99Bhk" failed: Invalid argument (22)

```

This same error was given for each of my Evolution folders. Evolution was not running at the time of backup. If it can't back up my mailstore, then this program isn't going to do the job. 

I'll tackle this again in the morning, been watching scroll bars too much tonight. 

eb

---

### Post by winotree on 2009-10-15
Hmm.  Sorry I can't answer this one for you -- I don't use *Evolution* and I've never received any errors while using *grsync*.  As it's the GUI for *rsync* perhaps you could look into it or wait for someone with  more knowledge and experience to help.  Hope you solve this before the weekend...

[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)
[http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)

---

### Post by jpkotta on 2009-10-15
This is what I use for back ups.  It's a script that our IT guy wrote, and I modified.  To use it, edit the section labeled CONFIGURATION, and put it into /etc/cron.daily with the following permissions:

```
-rwxr-xr-x    1 root     root         3792 May 15 13:56 rsync-backup
```

You probably want to set up an email MTA as well.  If not, you can just have it email to *user*@localhost.

```
#!/bin/bash

########################################################################
# rsync backup script
#
# To use this script, make it part of a cronjob and give it 755
# permissions.  You can set the various parameters below.  You can
# scatter files named ".rsync-filter" throughout the filesystem(s).
# They allow fine-grained control over what files are backed up.
# Obviously, read the rsync docs.

########################################################################
# START CONFIGURATION
########################################################################

########################################################################
# This is where all backups go.  There should be dated directories
# containing logs and deltas of old backups.  There will also be a
# directory called "current" which should contain mirrors of all the
# filesystems you are backing up.
destination_base="/media/backup"

########################################################################
# An email is sent to this address if an error occurs.  You should
# have mailx installed and some MTA set up.
MAILTO=user@example.com

########################################################################
# These two arrays list the filesystems you wish to back up.  They
# should really be an associative array, but I guess we'll have to
# wait for Bash 4.  

# This holds the name of the filesystems you want to back up.  This is
# mostly for the human perusing the backups.  It should be a good name
# for a directory.
declare -a filesystems
filesystems=( \
    "root" \
    "home" \
    )

# This holds the absolute paths to the filesystems you wish to backup.
declare -a sources
sources=( \
    "/" \
    "/home/" \
    )

########################################################################
# END CONFIGURATION
########################################################################

timestamp=$(date +%F)
this_host=`hostname`

function warning()
{
    msg="$1"
    sub="$2"
    if [ -z "$sub" ] ; then
	sub="Backup on $this_host failed!"
    fi

    #echo "$msg"
    echo "$msg" \
    	| mailx -s "$sub" $MAILTO
}

function error()
{
    warning "$1" "$2"
    exit 1
}

if [ ! -d $destination_base ] ; then
    error "Directory '$destination_base' does not exist."
fi

# This is the mount point of the filesystem of the destination.  If
# the destination is /var/backup, and /var is mounted as a separate
# filesystem than /, then dest_mount_point will be "/var".  Basically,
# we just want to make sure the filesystem is actually mounted so we
# don't fill up /.
dest_mount_point=`df $destination_base | grep -v Filesystem | awk '{ print $6 }'`
if [ "$dest_mount_point" == / ] ; then
    error "It appears that $destination_base's filesystem isn't mounted."
fi

for (( i=0 ; i < ${#filesystems[*]} ; i++ )) ; do
    filesystem="${filesystems[$i]}"
    destination="$destination_base/current/$filesystem"
    backup="$destination_base/$timestamp/$filesystem"
    source="${sources[$i]}"

    mkdir -p "$destination"
    mkdir -p "$backup"

    logfile="$destination_base/$timestamp/$filesystem.log"

    if [ ! -e "$source" ] ; then
	warning "Source directory '$source' does not exist."
	continue
    fi
    
    # Backup everything to destination
    # Any patterns found in .rsync-filter files are excluded
    # If it's not in source but is in destination, delete it in destination
    rsync --archive --force --ignore-errors \
	--quiet --log-file="$logfile" \
	--delete-after --delete-excluded --delete \
	--filter=': .rsync-filter' \
	--backup --backup-dir="$backup" \
	--one-file-system --sparse --stats --numeric-ids \
	"$source" "$destination" 

    if [ "$?" -ne 0 ] ; then
	warning "Something wrong with rsync command.  See '$logfile'."
    fi

    gzip $logfile

done

```

Example .rsync-filter file (for /).
```

- dev
- media
- mnt
- proc
- sys
- tmp
- var/run
- var/cache
- var/lib/mlocate

```

The .rsync-filter file syntax is explained in the rsync documentation.

---

### Post by Andavane on 2010-08-15
Not sure if this will help, but from a user who still feels Newbie-ish, what I do is look at the error list. Click the warning button to show you the errors. If it's only a few files, see if you really need them. In my case they are a few things  I don't need. Then delete those from the source file and synch again. It should now sync correctly.

Only works if you have a small number of files, of course.

This is not really a solution, but a "cop-out" which works.

I still don't know what this persistent problem is with me, but it's always the "Timestamp" thing. I'm keeping an eye out to understand the issue.

In your case you had 2,500 errors.

Perhaps you could have highlighted them and posted them. I reckon it would have been the same problem basically throughout.

---

