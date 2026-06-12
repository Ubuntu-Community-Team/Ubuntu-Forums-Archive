---
title: "backup to a specific usb harddrive"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by dsmryder on 2011-01-11
Hello all,
I'm a novice and I want to know if I could wright a script to allow my server to backup some files (pictures and music) to a specific hard drive. I am running ubuntu server 10.04, with Samba, Apache, Webmin, and how knows what else. The way I would like it to work is, I plug in the usb port, the server backs up the files, maybe does a revisions set, then when done, um, maybe send and e-mail or something. I am a novice, and I have like two hours a day to steal away from my family and work, not necessarily all at once. Any help would be greatly appreciated. Thank you in advance.

---

### Post by HDave on 2011-01-11
This is a very common practice and, with any luck, your script my be only one line long!

The program you'll want to use for this is rsync.  It's fast and reliable, but it has a zillion options and you'll need to review them very, very carefully.

Here is the call I make to rsync from within my own script:

rsync --progress --out-format='%o (%i) %n%L' --stats --human-readable --filter="merge $FILTER_FILE" --recursive --links --perms --times --delete --backup --backup-dir=$BACKUP_DIR "$SOURCE_DIR" "$DEST_DIR"

The items that start with a dollar sign ($) are script variables.  What this line does is very cool.  It mirrors the source_dir to the dest_dir, but any files that are deleted from dest_dir are moved to the backup_dir.  This makes restores or searching a snap.  It took me a while to get my head around it, but its awesome.

Good Luck!

---

### Post by HermanAB on 2011-01-11
Howdy,

As mentioned above, rsync is your friend.

However, since the HDD is a removable device, you have to make sure that it has a proper and unique Volume Label.  That will ensure that it will be mounted the same way each time you plug it in - otherwise, the mount point can change depending on what else is plugged in already, thus breaking your script.

---

### Post by dsmryder on 2011-01-18
First off, Thank you for you replies. secondly I'd like to say sorry for not responding earlier. I got froggy with my server, and took it out. Three days went by before I discovered that 
all I needed to do was to hit "s" to skip.
 
     rsync looks like the tool I will use to do my backups. I needed to figure out how to ID my HDD, and properly enter it in to my system. Yeay google. Now it's off to figure out how to adapt your script into my system.
 
     Once again, Thank you. coodos, coffee beans, cookies, or what ever is used on this forum.

---

