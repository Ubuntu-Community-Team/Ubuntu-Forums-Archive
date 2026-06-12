---
title: "GIMP edit and save permission problems"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by henry cow on 2010-08-01
I am having a problem with GIMP

Photos opened and edited, simple enough, but when I go to save, it refuses to do it and says that I do not have "permissions" etc to open and save a file.

These are ordinary .JPG photos taken with a camera that I am simply trying to crop. I am doing "Save As" with a different name and am not bothering the original at all. I have even tried saving it onto another partition.

What is the deal here? How do these originals get "locked" or whatever has happened to them?

Thanks !

---

### Post by llamabr on 2010-08-01
you tried saving them into your home dir?  You probably don't have permissions to save them back onto the camera.

---

### Post by henry cow on 2010-08-01
The originals and the potential saves are all on my NTFS partitions. These were all originally Windows files that I am working on in GIMP to try to learn and work myself away from Photoshop Elements.

I am the sole user of my computer, if I need permissions for some part of this, can I make a blanket grant?

Permissions, ownerships, users logging off and on, this is my greatest frustration and annoyance trying to navigate the Linux universe.

However, I understand that I am going to have to learn how to manage multiple users and permissions in the near future.

---

### Post by llamabr on 2010-08-01
Permissions are sometimes an annoyance, but they're there to keep users from messing with each other, and messing with the filesystem.  I'd think away from blanket permissions, because you're bound to mess something up.

In the meantime, use the system for what it's for.  When you try to save a new copy of the file you're editing, save it in your own home dir.  If you need to put it somewhere else, that's another issue, and we can show you how to make another partition or directory a member of your group.

---

### Post by henry cow on 2010-08-01
Cool. That worked. But now I will have to manually copy the file onto the NTFS drive if I want it there.

I have a monster desktop with 4 hard drives. They are 250GB, 500GB, and 1.5TB NTFS drives in single partitions, and an 80GB ext4 with 3 partitions (/, /home, and swap) for Ubuntu.

I fumbled around and got them to all mount automatically in Linux, but am I going to have to jump through more hoops to really use them?

For a variety of reasons, some business and some personal, I need to be about to read and write from everywhere to everywhere, (knowing that Windows won't write outside NTFS) that is why the overwhelming mass of storage is all NTFS.

What else do I need to do?

Thank you.

---

### Post by Paqman on 2010-08-01
> **henry cow said:**
> 
I fumbled around and got them to all mount automatically in Linux, but am I going to have to jump through more hoops to really use them?


Presumably you added entries to /etc/fstab for them to get them to mount. All you need to do is add an option to the lines in fstab specifying a particular user or group as the owner when they mount.

For example, if your user id is 1001, then add uid=1001 to the line. If you have multiple users on your machine you could assign them all to a group, then add gid=500 (or whatever the group number is).

---

### Post by miloE on 2010-08-01
hey sir.

try this:  open a terminal command window, and type

```
sudo gimp
```it will ask you for the ubuntu password again.  

this way you run gimp as root, and maybe with "god privileges" you will write your pictures wherever you want

soo..yeah, i strongly advise you to read about permissions...try here

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by llamabr on 2010-08-02
There's no good reason to run gimp as root.  A better strategy, if you need to write to other partitions, is simply to edit your /etc/fstab to make them writable.

---

### Post by henry cow on 2010-08-06
Thanks for your help. I would like to make them all writable, but do not know how. I would appreciate your help in that.

Now, I have another problem that is possibly tangentially related, probably, although totally different.

For the last few days, I have had a boot problem. I have a desktop with 3 NTFS hard drives and a Linux drive. Approximately one time out of 3, I get an error message on boot-up that "/dev/sdc5" is not ready, press "S" for skip or manually fix the problem.

Skipping usually does not work, and rebooting usually does. That is strictly a data disk and it is not required for booting either Windows or Linux. It is a fairly new Seagate 500GB in excellent condition. When it boots without mounting, obviously, I cannot get to it in Ubuntu (this never happens when I boot in Windows) but it contains all my .mp3 collection and family pictures as well, so I hate to miss it.

Is this a problem that is easily fixed? Sometimes it works fine.

Thank you.

---

