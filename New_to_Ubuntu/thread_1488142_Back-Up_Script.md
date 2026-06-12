---
title: "Back-Up Script"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by CSInDevelopment on 2010-05-19
I just wrote my first shell script and wondered what everybody thought of it?

```

#!/usr/bin/bash
# Script for updating System Onto partition mounted as "/media/Back_Up"
directory_list=`ls -1 /`
# loop all directories in /
for directory in $directory_list
do
    case $directory in
    
    "/cdrom")
        ;;

    "/home")
        ;;
    
    "/media")
        ;;

    "/mnt")
        ;;

    "/tmp")
        ;;

    *)
        echo "starting directory" $directory
        sudo tar -cvf /media/Back_Ups/$directory.tar /$directory
        echo $directory " complete"
        ;;
    esac
done
#inform user of completion
echo "Back up complete, in directory /media/Back_Ups/"

```

---

### Post by ubunterooster on 2010-05-19
I thought /tmp was temporary files? Do you need to back those up?

---

### Post by Darkness Des on 2010-05-19
That's a very good script. I created several of my own, except instead of only including certain things they include everything and only exclude things of my choosing. They also backup into a .tar.gz file, and it routes it through a symbolic link in my home folder that goes to an external hard drive.

---

### Post by CSInDevelopment on 2010-05-20
Well I like your idea to do the tar.gz so will do that next
How do I get the symbolic link to work?, just create a symbolic link from an external media to my home folder and direct it to there?

and also I didnt do /tmp (the cases except the last all get ignored  as my plan is to make back-ups so in event of errors I just re-install and then restore from the back-ups then restart...this would make for fast recovery of my system and anyone else's in event of intrusion.

---

### Post by Paqman on 2010-05-20
> **CSInDevelopment said:**
> the cases except the last all get ignored

So you're not backing up /home? :confused:

---

### Post by CSInDevelopment on 2010-05-20
I plan on this script being run just after updates running successfully, no point in backing up home as I have "work" and "multimedia" on seperate partitions making easier recovery in the event of system-error...home will just be a scratch-pad

---

### Post by Paqman on 2010-05-20
> **CSInDevelopment said:**
> I have "work" and "multimedia" on seperate partitions

Fair enough for data, but what about all your program settings, theme/Compiz settings, bookmarks, etc? Unless you back up home you'll have a completely default desktop when you restore.

---

### Post by CSInDevelopment on 2010-05-20
I use default.
I only change my shell so no point in the extra downtime over one line of code tbh
I dont use compiz e.t.c as I like to preserve the cpu time for development and testing as I want to become an open source developer in my free time, any pointers on that path?
I can already program some: c, c++, perl, java, html, css, javascript, php, asm.
I am about to self-teach python, and I have understanding of operating systems from bootstrap to memory management to POSIX subsystems :D

---

### Post by Paqman on 2010-05-20
> **CSInDevelopment said:**
> I use default.


Ah.

Compiz shouldn't adversely impact on CPU, btw. The whole point of a composited desktop is that all the work of rendering gets shifted from the CPU to your GPU.

---

### Post by CSInDevelopment on 2010-05-20
I didnt know that, thanks for the head's up on it
I just keep things plain though, probably just going to leave defaults for now because after windows 7 and vista I am not much of a graphics fan.

---

### Post by ragtag on 2010-05-20
Wouldn't changing

```
 sudo tar -cvf /media/Back_Ups/$directory.tar /$directory
```

to

```
 sudo tar -pcvfz /media/Back_Ups/$directory.tar.gz /$directory
```

save you some space and preserve your permissions.

Other than that, you might want to give rsync and hard linking a look. It let's you do incremental backup. This code should give you the general idea.
```

rsync -av --delete --exclude-from=filter.txt --link-dest=backup_destination/previous_copy backup_source backup_destination/date
```

What it does is hard link all files in the current backup, to those in the previous backup, and copy over only those that have changed. This takes up almost no extra space, and works pretty nicely. :)

---

### Post by ctimko on 2010-05-20
I have a faster one for you:
```

tar --pcvfz /{bin,boot,etc,home,opt,sbin,usr,var} bckp.tar.gz
```

:-)

---

### Post by ctimko on 2010-05-20
> **ubunterooster said:**
> I thought /tmp was temporary files? Do you need to back those up?

The switch case is for the directories he wants to skip. It's a good call on his part.

---

### Post by CSInDevelopment on 2010-05-20
> **ctimko said:**
> I have a faster one for you:
```

tar --pcvfz /{bin,boot,etc,home,opt,sbin,usr,var} bckp.tar.gz
```:-)

well what about the fact I have a folder I keep documentation of my work in to keep it out of my way but accessible? 

Anyway I enjoyed my way as it helped me learn shell scripting a little.

And I will definitely change to 
[FONT=monospace]tar --pcvfz

Plus I plan on making a "recover from back up" script for it to use on multiple systems and give to friends who dont install software they are not familiar with but trust me so making it more versatile. And easier to modify tbh :D

but it has frozen at "/proc/kcore" , is this expected?
[/FONT]

---

