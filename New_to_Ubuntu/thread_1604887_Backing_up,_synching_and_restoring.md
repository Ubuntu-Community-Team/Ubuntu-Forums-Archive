---
title: "Backing up, synching and restoring"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by simolokid4 on 2010-10-24
Dear Ubuntuforums.org

First of all, thanks for all the fast responses to all of my questions so far. I'm loving the community.

Now, as for my problem:

Hardware:
1 Desktop
1 Laptop
1 NAS (Ds210j, synology)

I'd like to use my NAS as backup facility.
Now, I have read the thread on this forum about backupping but I'm not sure how to do that with the NAS being on my network.

Also I'd like some pointers to create a cronjob that will take the changes of that day to my /home folder (where most daily changes happen im guessing) and write them to the backup on my NAS in my network. 

The backup doesn't need to be compressed or anything, since I've got loads of space on the thing anyway.

Now, since my Desktop and Laptop both have diffrent graphics drivers, will this result in problems? Since I'd love to have the same gui on my laptop and desktop.

Any idea where I should start?

Thanks a lot !

Simolokid

---

### Post by ArgusVision on 2010-10-24
Well, the software center and synaptic have backup/syncing apps available.
Some of them pre-suppose that there is a Unix/Linux distro on both ends(Client/Server). What type of OS does the NAS run? Is it a proprietary one that came installed? Also, What file system format is the NAS running?
Many run with ntfs, but some still use fat32.

---

### Post by simolokid4 on 2010-10-25
> Well, the software center and synaptic have backup/syncing apps available.
Some of them pre-suppose that there is a Unix/Linux distro on both  ends(Client/Server). What type of OS does the NAS run? Is it a  proprietary one that came installed? Also, What file system format is  the NAS running?
Many run with ntfs, but some still use fat32. 	
Last night I discovered the same thing, tough, didn't figure out how to automate that proces.

The nas runs a variant of Linux, I'm not sure what kind of filesystem tough.. I'm guessing ntfs or ext3 :<

Thanks for your reponse anyway :)

---

### Post by WitchCraft on 2010-10-25
One word: rsync.

You should investigate Windows shares and sshfs.
You need to (re)configure the share timeout for large files.

Other things:
[http://blogs.techrepublic.com.com/10things/?p=895](http://blogs.techrepublic.com.com/10things/?p=895)
[http://www.bacula.org/en/](http://www.bacula.org/en/)
[http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm](http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm)

---

