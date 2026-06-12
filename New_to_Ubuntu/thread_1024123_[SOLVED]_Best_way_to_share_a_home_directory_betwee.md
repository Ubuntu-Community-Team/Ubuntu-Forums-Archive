---
title: "[SOLVED] Best way to share a home directory between users"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-12-28
I have two users on an Ubuntu system. They don't have anything private, and will want to be able to access each others documents, photos, etc. Without blowing the permissions away, how can I share their entire home directory? I was thinking I could create a group that both users are in, but I'm not sure how to allow access. Do I need to chown the directories recursively? How about new file creation; is there a way for user paul to create a document using the group parents instead of paul automatically?

---

### Post by blueridgedog on 2008-12-28
Brainstorming:

1 - you could assign each user the same home director by editing /etc/passwd 
```

user1:x:1000:1000:user1 name,,,:/home/commonhome:/bin/bash
user2:x:1001:1000:user2 name,,,:/home/commonhome:/bin/bash
```

If you make the files group writable, it should work.

2 - The second option, would be to test out having the same user id for each in /etc/passwd

```
user1:x:1000:1000:user1 name,,,:/home/commonhome:/bin/bash
user2:x:1000:1000:user2 name,,,:/home/commonhome:/bin/bash
```

My brief search on the web indicated that this might work, but it would make password changes strange.

If you edit /etc/passwd, you will need to run:

sudo  /usr/sbin/pwconv 

To "remake" the shadow password file.

Note:  Editing /etc/passwd is what I would consider advanced and risky.  If you are not comfortable with a terminal, then perhaps other options should be explored.

My $.02

---

### Post by callan79 on 2008-12-28
> **jbrown96 said:**
> I have two users on an Ubuntu system. They don't have anything private, and will want to be able to access each others documents, photos, etc. Without blowing the permissions away, how can I share their entire home directory?


Hi There,

This does not answer your question directly, but just suggesting that sharing home directories is kind of messy.

I would be thinking that a dedicated disk or partition would be best. I've got this set up already, just for myself, but it would not be hard to change the permissions on the mount so that all users can write to it.

Changing permissions on home directories would be really risky - I've done it in the past, and I broke everything :(

As an example, I have two hard disks in my system, but you could do exactly the same thing with partitions on a single disk ...

80GB DRIVE:
 - 2GB swap partition
 - 20GB / (Ubuntu system files)
 - 40GB /home (Home directories for all users)

200GB DRIVE:
 - 200GB mounted on /media/storage

All users can access the /media/storage area, but each user only has access to their own home directory.

Also I have a Windows dual-boot on this computer for my video editing software. Windows can safely access the storage area, but I definitely do not want Windows touching my home directory!

So each user can change their own password without breaking anything.

Also when it comes time for backups or re-install to new Ubuntu version, backups and things are a lot tidier.

Of course the downside, is you have to either re-partition your drive, OR go and buy another hard disk for this purpose.

Good luck, post back if you need any more pointers :)

Cheers
Callan

---

### Post by jbrown96 on 2008-12-29
Thanks for the replies. I did the group method though, and it is working very nicely. 

I have two users janice and paul, so I added them to each other's group with these commands
```
sudo usermod -a -G paul janice
sudo usermod -a -G janice paul
```
Then I changed the permissions recusively on each of their home folders to allow group members full access. 
This does violate some security to allow users access to one another's group, but it works great for my parents.

---

