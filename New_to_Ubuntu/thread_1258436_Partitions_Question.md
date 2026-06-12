---
title: "Partitions Question"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by mattsid1 on 2009-09-05
When I installed Ubuntu 9.04 I decided to manually select my partitions and did the following.

Root partition ext 3 '/' 7gb
Swap partition 'swap' 4gb (yep found out later this is probably way too much, but no harm done!)
Home partition '/stuff' 40gb

I have no Windows on my computer, just Ubuntu

I called the home directory 'stuff' just so it would be easy to find, or so I thought. My home directory 'stuff' seems to be located in the file system along with etc, usr, bin and all those system files and directories, and is read only so I have no disk space.

Did I do something wrong? If so can it be corrected. Also I don't mind sticking the Live CD in again and starting from scratch if it means doing it properly, but if there is a work around I'd appreciate any help. 

Thanks in advance.

---

### Post by pastalavista on 2009-09-05
Just put in the CD and reformat the /stuff partition and rename it to /home

---

### Post by woedend on 2009-09-05
You can check /etc/fstab to make sure its not being mounted with option ro.   Can you write to the drive as root(using sudo)?  I have my system setup very similar to yours and I keep it that way.  I don't want some malicious code or typo on my part wiping out my "stuff"(called "files" on my pc...we're so original lol).  This way I can listen to music or watch videos when I please...but to add files to it I do so with sudo mv or sudo nautilus(although some will swear against this..meh).
In this particular case if you want user permission to write, you should read up on chmod/chown(i don't particularly like the idea of giving exact syntax as this is something good fundamentally to know for later).

---

### Post by jnorthr on 2009-09-05
if it were me, i'd remove the swap partition. Then divide the 4gb into a small swap like 1gb and also i think you must have a partition marked as '/home' so ubuntu will work correctly as it's the folder in which you have the 'user' subfolder which holds all your settings, etc.
mine looks like /home/users/jim

once your network comes up, that is, attaches to the internet, you can begin to look at all the music sharing things you can do to stream music to your other systems in your house from /Stuff   :o

---

### Post by woedend on 2009-09-05
/home doesn't need to be on its own partition.  I've never liked the idea of keeping config files and whatnot when doing upgrades or switching between distros.  Not that having /home on its own partition is bad, it's just not necessary.  It gets created on the root partition.

---

### Post by mapes12 on 2009-09-05
> **woedend said:**
> /home doesn't need to be on its own partition.  I've never liked the idea of keeping config files and whatnot when doing upgrades or switching between distros.  Not that having /home on its own partition is bad, it's just not necessary.  It gets created on the root partition.
The only problem I find with /home being on the same partition as "/" is that when upgrading as I did recently from 8.04 to 9.04 the easiest way to go was a clean install (otherwise I would have to ask Update manager to go through 8.10 and then to 9.04...........and that's if it didn't crash). With /home on its own partition all my settings like my wallpaper, FF bookmarks and Addons and my sound preferences are all good to go straight from the off. Otherwise I would have to manually set everything up again (that's if I could remember all my tweaks).

For the OP I would start again but this time when going through the Partitioning section using manual select that big partition to be /home from the list of options. Once the system us up you can create a /stuff folder inside /home/user or you could create a new home account for "stuff".

Also, put swap at the end not in the middle so from the left hand side of GParted you would have the partitions in this order:

/
/home
/swap

---

### Post by louieb on 2009-09-05
Years ago when Jerry Jones was trying to get Deon Sanders to play for the Dallas cowboys. Jerry said to Deon what do you want? - 12 or 13 million. Deon said both. 

I have both a separate /home and a data partition. 

I have a small separate /home partition. Used to be 2GB but got generous when I got a much bigger hdd now its 5GB. I consider /home to be a part of the OS and I want my data on a separate partition - . most of my drive space is given to a partition mounted on /media/stuff  
Heres its /etc/fstab entry

```
/dev/sdb1      /media/stuff    ext3    defaults          0       2
```I gave everybody full access with the command ```
sudo chmod 777 /media/stuff
```the ls -l shows that
```
drwxrwxrwx 26 root root 4096 2009-08-30 05:06 stuff
```

But if I had to choose one or the other I would have a separate data partition. Leaving /home in the / (root) partition. I can alway backup /home to my data partition when reinstall or upgrade time come around.

---

