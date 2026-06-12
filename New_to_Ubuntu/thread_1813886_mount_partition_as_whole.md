---
title: "mount partition as whole"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by avnd on 2011-07-28
Hi there!

On my system, I have all my data on a separate partition (/dev/sda3) (labelled DATA). Usually I access them by just clicking on them in the file manager. That automatically mounts them. I can see the partition on the /media folder residing as a folder called 'DATA'.

This time round, I thought I'd try accessing my files from the terminal. I typed in 
"sudo mount /dev/sda3 /media"

Previously, I remember that when I ran this command (I might be wrong about this), I was able to see the DATA partition residing as a single folder called 'DATA' under '/media'.

But now, when I run the command, all I see is the subfolders of DATA under the /media folder. I can't see the bigger DATA partition as a whole.

What is the correct way to do that from the terminal?

---

### Post by diesch on 2011-07-28
If you want to mount the disk at */media/DATA* you have make sure that the folder */media/DATA* exists and use
```
sudo mount /dev/sda3 /media/DATA
```

---

### Post by oldfred on 2011-07-28
diesch is correct, but you may have to create the mount point of /media/DATA first. You have been mounting using the label which is not an automatic mount point when you manually mount it. If you have used /media/DATA as a mount before it may still be in the list of mount.

If you want to permanently mount it every time your reboot you can add the mount to fstab.

# mountdisk.txt
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I just learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod 777 /data
sudo chown $USER:$USER /data
#where $USER should be your login name
#or to see user
echo $USER

---

### Post by avnd on 2011-07-28
Thanks for your replies, guys. But I still have doubts.

1. I'll rephrase my question this time. When I double click on my 'DATA' partition on Nautilus, it automatically gets mounted on '/media'. I only see it as a folder going by the name 'DATA' (the label of the partition). Now, this double-click must be a substitute for a command which I should be able to run from the terminal. What is that command?

2. There's another thing I noticed only now. I have a folder called 'GRUBpartition' in my '/media' folder. When I run
sudo mount /dev/sda3 /media
that 'GRUBpartition' folder vanishes. Is this normal and why is that?

Cheers!

---

### Post by CatKiller on 2011-07-28
> **avnd said:**
> why is that?

Because you keep mounting a different partition over the top of it. Stop mounting it to /media and mount it to /media/Data if you don't want it to cover the other contents of /media.

---

### Post by avnd on 2011-07-29
> **avnd said:**
> 

When I double click on my 'DATA' partition on Nautilus, it automatically gets mounted on '/media'. I only see it as a folder going by the name 'DATA' (the label of the partition). Now, this double-click must be a substitute for a command which I should be able to run from the terminal. What is that command?



I'm still waiting for an answer for that question. Anyone? :)

Cheers!

---

### Post by Morbius1 on 2011-07-29
Your question has already been answered. Let me try it a different way:

> **avnd said:**
> On my system, I have all my data on a separate partition (/dev/sda3) (labelled DATA). Usually I access them by just clicking on them in the file manager. That automatically mounts them. I can see the partition on the /media folder residing as a folder called 'DATA'.
What the system will do without you realizing it is this:
* It creates a mount point at /media/"LABEL of partition"
* It mounts the partition to that mount point
* When you unmount it it will remove that mount point

> This time round, I thought I'd try accessing my files from the terminal. I typed in "sudo mount /dev/sda3 /media" ... But now, when I run the command, all I see is the subfolders of DATA  under the /media folder. I can't see the bigger DATA partition as a  whole.It's doing exactly what you told it to do. It's mounting sda3 to /media itself. If you want to recreate what the system will do then recreate it's steps:

```
sudo mkdir /media/DATA2
``````
sudo mount /dev/sda3 /media/DATA2
```It has to be DATA2 because you are mounting this temporarily. If you create a permanent folder at /media/DATA and then later use the file manager approach to mount it it will mount to /media/DATA_ which will be confusing since you will see both /media/DATA and /media/DATA_.

---

### Post by diesch on 2011-07-31
> **avnd said:**
> Thanks for your replies, guys. But I still have doubts.

1. I'll rephrase my question this time. When I double click on my 'DATA' partition on Nautilus, it automatically gets mounted on '/media'. I only see it as a folder going by the name 'DATA' (the label of the partition). Now, this double-click must be a substitute for a command which I should be able to run from the terminal. What is that command?


```
 udisks --mount /dev/sda3  
```

---

### Post by avnd on 2011-08-15
Thanks a ton, diesch. It was exactly what I wanted.

---

