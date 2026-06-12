---
title: "Complete Back-up Help?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by scottishbloke on 2010-06-06
Hi folk's, I want to know how to do a complete back-up on lucid lynx please, I have never done this before so step by step guidance would be great and thanks.

---

### Post by acrazyplayer on 2010-06-06
Well you can do a few things but the best would be to reinstall any programs as permissions may become awkward if anything changed. 

Just back up all your important files like firefox bookmarks, pictures, videos, music, and maybe anything you downloaded. If you have a lot of text files then the best thing to do would be to put them all in one folder and then compress them. Just right click on the folder and hit "compress" then choose okay. I wouldn't bother trying to compress anything else as movies, music, and pictures are usually already compressed.

---

### Post by mapes12 on 2010-06-06
What I do:-

Keep /home on its own partition and back it up on an external HDD using Grsync. If my system crashes I just reinstall the Ubu OS to its separate partition, apply updates and any other apps I need and within 20 mins I'm up and running again.

If you want to keep an image of your entire drive try Clonezilla.

There are hundreds of ways of backing up an Ubu system.

---

### Post by Barrucadu on 2010-06-06
Warning: This may be way above your head, I'm not too good at explaining :P

I use rsync for my backups, I wrote a script the other day which creates a full backup at the beginning of every month, and an incremental backup storing the changes between now and the last full backup (so not quite an incremental backup, which would just be the changes between not and the last incremental backup).

The basic syntax for an rsync command is this:
```
rsync /source /dest
```

Which copies all differences between source and dest to make dest an identical copy (barring any new files in dest, which remain there). A more complex command would be this:
```
rsync -a --delete /source /dest
```

That's the basic form for creating a system backup. The **-a** flag enables a load of other options (preserving permissions, file ownership, and a plethora of other stuff you need), and **--delete** deletes files in dest which are not in source.

Of course, you don't want to backup everything. Some things make no sense to back up, so that is where **--exclude** comes in:
```
rsync -a --delete --exclude=/proc --exclude=/dev --exclude=/sys --exclude=/media/backup / /media/backup
```

That'd back up / to /media/backup, ignoring /proc, /sys, /dev, and the backup device itself.

Here's the command I use to generate a full backup:
```
rsync -avz --numeric-ids --delete --exclude-from=/etc/backup.exclude --stats / "/media/BackupHDD/`hostname`/`date +%Y-%m`/"
```

The **--exclude-from=** argument specifies an excludes file, which has a very simple syntax. Mine is displayed below:
```
# Include
+ /dev/console
+ /dev/core
+ /dev/fd
+ /dev/fuse
+ /dev/kmsg
+ /dev/loop0
+ /dev/net
+ /dev/null
+ /dev/ppp
+ /dev/pts
+ /dev/shm
+ /dev/stderr
+ /dev/stdin
+ /dev/stdout
+ /dev/zero

# Exclude
- /dev/*
- /dev/pts/*
- /proc/*
- /sys/*
- /tmp/*
- /media/*
- /mnt/*
- /share/*
- /var/abs/*
- /var/lib/pacman/sync/*
- /var/lib/clyde/sync/*
- /var/cache/linhurd
- /var/cache/pacman/pkg/*
- /home/barrucadu/projects/gnu/www
- /home/barrucadu/hurd/ahurd.iso
- /home/barrucadu/hurd/swap.img
- /home/barrucadu/packages/*/src
- /home/barrucadu/packages/*/pkg
- /home/barrucadu/tmp/*
- /home/barrucadu/.config/zcompdump*
- /home/barrucadu/.config/thumbnails/*
- /home/barrucadu/.config/opera/cache/*
- /home/barrucadu/.config/opera/icons/*
- *lost+found
```

**-v** makes rsync verbose, **-z** uses compression during the transfer, **--numeric-ids** transfers UIDs and GIDs as numbers rather than names, and **--stats** shows statistics of file transfer.

Now, the command I use to generate an incremental backup:
```
rsync -avz --numeric-ids --delete --exclude-from=/etc/backup.exclude --stats --link-dest="../`date +%Y-%m`" / "/media/BackupHDD/`hostname`/`date +%Y-%m-d`/"
```

This introduces a new option, **--link-dest**. This is a truly magical option. All unchanged files between the destination and the link-dest, are hard linked to the link-dest. This means that, in my incremental backups, I still have a full filesystem hierarchy, but it only takes up as much space as there are changes.

Of course, my full backup script is a bit more complex than that; it allows for backups over SSH, for example. The full script is [here](http://github.com/Barrucadu/home/blob/master/bin/backup) if you want to have a look.

---

### Post by ajgreeny on 2010-06-06
> **mapes12 said:**
> What I do:-

Keep /home on its own partition and back it up on an external HDD using Grsync. If my system crashes I just reinstall the Ubu OS to its separate partition, apply updates and any other apps I need and within 20 mins I'm up and running again.

If you want to keep an image of your entire drive try Clonezilla.

There are hundreds of ways of backing up an Ubu system.
+1
In theory grsync is not a proper backup application according to some people, but I have always ignored that and used it with great success to keep an incremental backup of everything in my home partition on a USB external drive.

It's quick, simple and will make sure you have everything that you need.  Some users suggest that it is helpful to backup some filesystem folders such as  /etc and /usr as well, as they contain configuration for some applications, but I have never bothered with that.  /home is all I need!

---

### Post by scottishbloke on 2010-06-06
Right I've been playing with remastersys for 2 and a half hours and I think I've got the hang of how it works. I've tested it and all seems well, But once I've restored and I go to administration Theres something saying about "Install custom" But I've already installed to my harddrive?

Is there something i should be removing once the restore is done?

---

### Post by HankB on 2010-07-01
> **Barrucadu said:**
> 
I use rsync for my backups, ...

Of course, my full backup script is a bit more complex than that; it allows for backups over SSH, for example. The full script is [here](http://github.com/Barrucadu/home/blob/master/bin/backup) if you want to have a look.

Thanks for the mini-tutorial and the script. I've used rsync to backup my home directory, making a daily copy that overwrites the one on the same day of the previous month and then on the first of the month, renaming the copy so that it doesn't get overwritten. That gave me daily copies going back one month with monthly copies that did not get erased. I didn't know about the '--link-dest' option so now I can save some space using that.

I'm reviewing backup options at the moment because I'm getting ready to set up a NAS at a remote location which I'll access over the Internet. In fact, the NAS will be a standalone box running Ubuntu Server and will hold two mirrored drives.

Last question - if you're listening - is this likely to be my best backup solution? I was hoping to find a pointer to an article or wiki that would list popular backup programs and the strengths or weaknesses of each.

Finally, thanks for using ISO 8601 compliant date formats. :D

---

