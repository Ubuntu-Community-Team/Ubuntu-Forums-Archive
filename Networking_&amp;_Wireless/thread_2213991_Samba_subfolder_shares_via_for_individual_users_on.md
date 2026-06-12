---
title: "Samba subfolder shares via for individual users on different HDD"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by sean40 on 2014-03-29
Hello People of Linux, I am Running Ubuntu 12.04 LTS 64 bit on my machine and i have set up some samba shares already but what i want to do is a little tricky for me to try and grasp and im not sure if there is a way on how to do what im looking for.

Instead of having home shares for users in the ~ Home directory i want to have the user shares on a different drive.  I want to do this to limit the space on the primary Linux Operating disk and place all my data in the 4TB drive i have installed with the rest of all my media i have on it.

Linux is running on a 128GB SSD and i dont want to fill that up, instead i want to place it on the media drive i have

My question: Is there a way to move the directories of users to the other hard drive i have EX: "/media/HDD1/Documents" instead of having them in the ~ Home Directory which is on the installation SSD
     Or is there a way to use sambe to have folders when users create them in "/media/HDD1/Documents" that only that user can get into and create and modify files they put in their own folder



p.s. i have samba 3.6.3 on my machine

---

### Post by bab1 on 2014-03-29
> **sean40 said:**
> Hello People of Linux, I am Running Ubuntu 12.04 LTS 64 bit on my machine and i have set up some samba shares already but what i want to do is a little tricky for me to try and grasp and im not sure if there is a way on how to do what im looking for.

Instead of having home shares for users in the ~ Home directory i want to have the user shares on a different drive.  I want to do this to limit the space on the primary Linux Operating disk and place all my data in the 4TB drive i have installed with the rest of all my media i have on it.

Linux is running on a 128GB SSD and i dont want to fill that up, instead i want to place it on the media drive i have

My question: Is there a way to move the directories of users to the other hard drive i have EX: "/media/HDD1/Documents" instead of having them in the ~ Home Directory which is on the installation SSD
     Or is there a way to use sambe to have folders when users create them in "/media/HDD1/Documents" that only that user can get into and create and modify files they put in their own folder



p.s. i have samba 3.6.3 on my machine

Here are some general guidelines regarding the Linux [URL="http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"]File System Hierarchy 
[/URL].

I put all the shared data at /srv/<some_directory>.  I would do something like this:

[LIST]
[*]Partition the 4 TB as 2 ( maybe 2 of 2TB) 
[*]mount one partition at /home and put the users home directories there
[*]Mount the other partition at /srv/share and create Samba shared directories for remote access
[/LIST]
Then the only thing on on the SSD is the OS.  You don't need symlinks or other complications.  The user sees their home directory as normal.

[COLOR="#0000FF"]Edit:  Samba provides a share called [homes] that allows the user to have remote access to their personal data on a server. [/COLOR]

---

### Post by sean40 on 2014-03-29
ok thank you very much for your help. LOL its going to be a pain to grab all the data off the drive because the drive is currently in one partition, but ive done it once before.

---

### Post by bab1 on 2014-03-29
> **sean40 said:**
> ok thank you very much for your help. LOL its going to be a pain to grab all the data off the drive because the drive is currently in one partition, but ive done it once before.

If you have the room just resize the partition you have and add a second partition.  After formatting the FS on the new partition remount then where they belong.  The home directories will need the data moved for sure as you are going to mount one of the partitions at /home.  Nothing should be in that directory when the new partition is mounted.

Use UUID's in the fstab for partition ID.

---

### Post by apohal9 on 2014-03-29
> **bab1 said:**
>  
[LIST] 
[*]mount one partition at /home and put the users home directories there 
[/LIST]
   This should be the simplest option to have all the home folders for samba users on an exclusive harddisk.

---

### Post by bab1 on 2014-03-29
> **apohal9 said:**
> This should be the simplest option to have all the home folders for samba users on an exclusive harddisk.

Well, at least on a separate partition.  The disk the OP will have 2 partitions.  One for the homes and another for any shared data.

---

### Post by apohal9 on 2014-03-29
> **bab1 said:**
> Well, at least on a separate partition.  The disk the OP has will have 2 partitions.  One for the homes and another for any shared data.

Sure, your answer is more specific. At least on a separate partition.

---

