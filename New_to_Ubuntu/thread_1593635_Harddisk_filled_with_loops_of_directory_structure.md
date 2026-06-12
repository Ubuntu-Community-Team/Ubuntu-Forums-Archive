---
title: "Harddisk filled with loops of directory structure"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Maddog59 on 2010-10-11
Hi there,

I'm not sure this is an Absolute Beginner's question, but as I am a beginner at Linux/Ubuntu, I'm putting my problem into this forum.

Have a server with v8.10 installed.  The server is normally overseen by an administrator, who for various reasons, cannot attend to this problem for a few weeks.

It appears the server has kept writing the same files to the harddisk in consecutive loops, and this has filled up the HD, as when we try to access data from other workstations, we are getting error messages saying the disk is full.  The Disk Usage Analyzer confirms the HD is (for all practical purposes) full

The exact problem is not obvious, but it appears that occasionally the Simple Backup (v0.10.4) does not write its stuff to the appropriate backup disk, instead writing another loop of files.

This loop appear to be as follows. /proc/self/root/proc/self/root etc  This goes **at least **15 levels down and includes all the other files and folders including a 1GB Backup Error file in the /Dev folder which also appears at each level.

Simple solution would be to delete all the loops, however the system will not let me do that.  I have tried giving myself all admin rights in the Users & Groups function - however I still get error messages saying "Error removing file: Permission Denied" or "The folder "zzz" cannot be handled because you do not have the permissions to read it" 

Having used Unix for a while (20-something years ago) I'm not too scared of the Command Line and was able to figure out the required commands.  I even used the 'sudo' prefix.  But all I get is "Operation not Permitted" or "Permission Denied".

Unless I can figure out how to delete these repeating loops of folders, we are unable to access any of the data on out harddisk.

Can anyone please help with what i need to do to delete these loops, and/or offer any insight as to why Simple Backup writes this rubbish rather than writing the files that are marked for backup to the backup disk.

All advice gratefully appreciated

---

### Post by ubunterooster on 2010-10-11
snip

---

### Post by oldfred on 2010-10-11
I know little about this but it looks like /proc is just about running tasks. I look at mine /proc/self at it is a link to a number in /proc and I have a bunch of numbers in /proc.

[http://www.linux.com/archive/articles/126718](http://www.linux.com/archive/articles/126718)

Something in your backup must be miss configured and looping as you are running. If you kill the backup process does it change things?

---

### Post by sisco311 on 2010-10-11
Hi and welcome to the forums!

/proc & /dev are virtual filesystems. /proc/self/root is just a symbolic link to the root directory ("/"), so there is nothing wrong with that.

By default, simple backup stores the backup(s) in /var/backup. Check that dir first.

---

### Post by Maddog59 on 2010-10-11
Thanks for the suggestions

**sisco311**, the directory for the backups is a custom dir - /media/backupdrive.  It is empty at the moment.  The /var/backup dir has 13 files for 4.8Mb - nothing untoward there I suspect.

I understand how the Process directory works - in Windows terminology, it is a merge between the Temp folder and the Process Monitor in the Task Manager.  I seem to remember something similar in Unix, but cannot remember its name.

I also understand that the dir creates itself on bootup, and re-creates itself virtually every time a new process is started.  Is this why I am unable to delete any sub-directories?

Nevertheless, it makes no sense that the dir  sets up an un-ending loop that only stops when disk space runs out.  For what its worth, Disk Usage Analyzer shows: *Total filesystem capacity :183.3GB (Used:179.9GB Available:3.4GB)*

This is more than just "virtual" loops!

I have had a reasonably good look through the directory structure, but cannot see any other obvious loops occurring.

**oldfred**, Thanks for your link to the article explaining the /proc directory better than I could previously understand it.

Simple Backup is pretty basic.  The directories scheduled for backup seem to be correctly shown in the Include/Exclude tabs.  The Destination folder is correctly set - I have just checked the "Abort backup if Destination Directory does not exist" option - although I can't see this making a lot of difference!

I'm afraid that killing the backup process now is too little too late - the HD is FULL, stays full after re-booting, and I can't see how to resolve the problem

Maddog (59)

---

### Post by sisco311 on 2010-10-11
Take a look at this [thread=1122670]HOWTO: Recover Lost Disk Space[/thread].

---

### Post by Maddog59 on 2010-10-11
**sisco311**,  Thanks for the new link.  I'll need to go through it carefully.  Unfortunately, I'm in the UK and as it's past midnight, I'm not far off turning into a pumpkin.  I'll go through the link fully tomorrow morning - hopefully that and a clear head will do wonders for the HD.

MadDog (59)

---

