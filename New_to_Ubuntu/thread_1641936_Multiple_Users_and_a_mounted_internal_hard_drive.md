---
title: "Multiple Users and a mounted internal hard drive"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by ForkboyInk on 2010-12-09
Hi I've searched as many combos of my issue as I can think of but no clear answer seems to be available. So here goes...

I have ubuntu 10.10 loaded on an old Compaq (works well) but I have it set up for my girls, I have the admin account and they have limited user accounts. I have a 2nd hard drive internally mounted and it's configured for a media drive (dev/sdb1) and I can't seem to get it to mount automatically for them when they login. It keeps asking for my password for them to access it. I have used the admin control to create a group called "family" and given both their accounts permission to read/write to that drive and I also changed there main groups to "family" so they should have access but every time the system shuts down we have to go through the password issue again. Any thoughts?

---

### Post by deanjm1963 on 2010-12-09
This might work as it does for my external. It allows three of us to write to it.

Substitute my name with yours. My external is called "removable", I'm sure you've made a name for your drive.

```
sudo chown -R dean:users /hardrive-name
sudo chmod -R 755 /hardrive-name

```
Give that a try. Hope this helps.

Also if you've ext3/4 as your file system also do


```
sudo tune2fs -m 0 /dev/sdb1
```

That will give you more disk space by removing the "5% allocated for root" - not needed on a data partition

---

### Post by ForkboyInk on 2010-12-09
> **deanjm1963 said:**
> This might work as it does for my external. It allows three of us to write to it.

Substitute my name with yours. My external is called "removable", I'm sure you've made a name for your drive.

```
sudo chown -R dean:users /hardrive-name
sudo chmod -R 755 /hardrive-name

```
Give that a try. Hope this helps.
Nope That didn't solve it Thanks anyway. I still have to put in my password before they can mount it to their desktop. Any other suggestions?

> Also if you've ext3/4 as your file system also do


```
sudo tune2fs -m 0 /dev/sdb1
```

That will give you more disk space by removing the "5% allocated for root" - not needed on a data partition
I'll try this next (missed it the first time)

---

### Post by ForkboyInk on 2010-12-09
Thanks Dean but no luck. I am going to troll through the security discussions section again and see if there is anything remotely close to what I'm trying to do here. 

Still open to suggestions though...

---

### Post by oldfred on 2010-12-10
I have not done it but saved some links. You need to learn about groups and those kind of settings as you are a group.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

---

