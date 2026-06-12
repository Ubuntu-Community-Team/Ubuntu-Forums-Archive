---
title: "how to create back up"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by chitragurung on 2010-11-05
Hello,

I have Dell Inspiron Mini v with Ubuntu 8.04 I want to create back up whole system in external drive how can I create it ?

---

### Post by sikander3786 on 2010-11-05
This is the oldest yet the best method I still use for backing up my install.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Some more options here.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

If you want a gui with Live CD, Clonezilla is a mighty powerful backup software.

[http://clonezilla.org](http://clonezilla.org)

---

### Post by cipherboy_loc on 2010-11-05
Personally for my backups I use a squashfs filesystem. I do this in the following way:
(Commands are in red)

1) Get a Live CD or a Live USB key, and boot it to a live environment. 
2) Mount the root drive ([COLOR=Red]sudo mount -t [/COLOR](type of filesystem that / resides on) [COLOR=Red]/dev/[/COLOR](name of the drive. If / is on your first drive and its on the first partition, then the name would be sda1) [COLOR=Red]/mnt[/COLOR] (In my case, [COLOR=Red]sudo mount -t ext4 /dev/sda5 /mnt[/COLOR]))
3) Mount a smb share, or other place to back up your drive to (I use an external USB drive) 
4) [COLOR=Red]sudo apt-get install squahsfs-tools[/COLOR] -- Installs the tools for making squashfs archives.
5) [COLOR=Red]mksquashfs /mnt/* /path/to/external/device[/COLOR]
6) Wait.... and wait.... etc...


To restore from a back up:

(Commands are in red)
(Steps 1 through 3 are the same as above)
4) CD to the directory where your squashfs archive is.
5) [COLOR=Red]mkdir mnt[/COLOR]
6) [COLOR=Red]sudo mount -o loop ./squashfs_archive_name mnt[/COLOR]
7) [COLOR=Red]sudo rm /mnt/*[/COLOR]
8) [COLOR=Red]sudo cp -prv ./mnt/* /mnt[/COLOR]



Cipherboy

---

