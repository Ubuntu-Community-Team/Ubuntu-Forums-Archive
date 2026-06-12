---
title: "permissions... ssh permissions"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Balinsky on 2007-05-13
here is the story: one network two fiesty computers. One is my laptop one is my bros PC. I plugged my external hard drive into my bros pc and want to be able to mount it on the laptop. I have SSH working between the two computers. I can navigate most of the file structure via SSH. 

but when I try to go to /media/XHD it wont let me
```

$ cd XHD
-bash: cd: XHD: Permission denied

```

any pointers would make my day
JeBsky

---

### Post by mssever on 2007-05-14
> **Balinsky said:**
> here is the story: one network two fiesty computers. One is my laptop one is my bros PC. I plugged my external hard drive into my bros pc and want to be able to mount it / access the files. I have SSH working between the two computers. I can navigate most of the file structure via SSH. 

but when I try to go to /media/XHD it wont let me
```

$ cd XHD
-bash: cd: XHD: Permission denied

```any pointers would make my day
JeBsky

First, I don't understand what SSH has to do with your problem. Can you elaborate?

What filesystem is /media/XHD formated as? ext3? FAT32? NTFS? Fixing permissions problems is different if you're using a filesystem that doesn't understand Linux/UNIX permissions (e.g., anything from Microsoft).

Finally, what is the output of ```
ls -dl /media/XHD
``` and ```
ls -dl /media/XHD/*
```

---

### Post by Balinsky on 2007-05-14
its fat 32 its been plugged into my lappy for a couple months now

the first ones output:
```

drwx------ 9 tv root 32768 1969-12-31 19:00 /media/XHD

```

the second:
```

ls: /media/XHD/*: Permission denied

```

And i dont know if ssh has anything to do with the problem.

thanks

---

### Post by mssever on 2007-05-14
> **Balinsky said:**
> its fat 32 its been plugged into my lappy for a couple months now

the first ones output:
```
drwx------ 9 tv root 32768 1969-12-31 19:00 /media/XHD
```the second:
```
ls: /media/XHD/*: Permission denied
```And i dont know if ssh has anything to do with the problem.

thanks

I don't think that SSH has anything to do with your problem, except that I'm guessing the primary username on the desktop is tv and is different from the primary username on your laptop.

You can't set permissions on individual files on the FAT32 filesystem, because FAT32 doesn't support permissions. So, you have to specify permissions for the entire partition. You do this in /etc/fstab. See [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131") for details.

The easiest--but not the most secure--solution is to set the umask to 000. That means that everybody has full control of the files. Here's an example: ```
/dev/hda5       /media/fat32    vfat    defaults,utf8,umask=000,gid=46 0       1
```

---

### Post by Balinsky on 2007-05-15
k i didnt explain what i wanted to do well enough i want to be able to mount the external hard drive that is plugged into the pc on my laptop(across the network) i thought ssh would me the easiest way to do this it is proving not to be.

---

### Post by mssever on 2007-05-15
> **Balinsky said:**
> k i didnt explain what i wanted to do well enough i want to be able to mount the external hard drive that is plugged into the pc on my laptop(across the network) i thought ssh would me the easiest way to do this it is proving not to be.

For that, you need either Samba or NFS. Samba works with both Linux and Windows; NFS is Linux-only (but preferable in a Linux-only situation). If you're transferring outside of your local network, Samba probably won't work too well (I'm no Samba expert, though). If you use NFS across the Internet, you should run it through an SSH tunnel for security.

I can try to help you more specifically, but I need to know which computer the external HD is attached to: XP or Linux? And, you said that you want to access it from outside your local network, right?

EDIT: I think that I've confused your issue with another thread I'm involved with. You're running two Feisty computers and just the local network? If so, that simplifies matters greatly.

---

### Post by Balinsky on 2007-05-15
Yes, there are two fiesty computers.

the reason i tried to use ssh in the first place is because samba is/was being a complete pain in the ***.

I have the XHD shared via samba on my brothers computer
but when i go into nautilus and try to navigate too it (smb://PC/XHD)
i get the fun little error message:
```
The folder contents could not be displayed.
Sorry, couldn't display all the contents of "XHD".

```
But currently on the ssh side of things i almost have it working (i think)
i used sshfs [en.wikipedia.org/wiki/SSH_Filesystem]("http://en.wikipedia.org/wiki/SSH_Filesystem")
and mounted it at (on the laptop) /media/XHD

I thought i had it but when i navigate to it with nautilus i get
```
Couldn't display "/media/XHD".
The attempt to log in failed.

```
which makes no sense to me since if i do a 
$ gksudo nautilus
and then navigate there it works just as it should

permissions are tearing me up everywhere it looks like

again
jeBsky

---

### Post by mssever on 2007-05-16
> **Balinsky said:**
> Yes, there are two fiesty computers.

the reason i tried to use ssh in the first place is because samba is/was being a complete pain in the ***.

I have the XHD shared via samba on my brothers computer
but when i go into nautilus and try to navigate too it (smb://PC/XHD)
i get the fun little error message:
```
The folder contents could not be displayed.
Sorry, couldn't display all the contents of "XHD".

```But currently on the ssh side of things i almost have it working (i think)
i used sshfs [en.wikipedia.org/wiki/SSH_Filesystem]("http://en.wikipedia.org/wiki/SSH_Filesystem")
and mounted it at (on the laptop) /media/XHD

I thought i had it but when i navigate to it with nautilus i get
```
Couldn't display "/media/XHD".
The attempt to log in failed.

```which makes no sense to me since if i do a 
$ gksudo nautilus
and then navigate there it works just as it should

permissions are tearing me up everywhere it looks like

again
jeBsky
You'll probably have to set the umask in fstab as I mentioned earlier.

For networking, NFS is the simplest way to go. On your server, install nfs-kernel-server; install nfs-common on the client.

On the server, edit /etc/exports and add an entry for your external disk (and anything else you might want to share. Type ```
man 5 exports
```for documentation. As an example, here's my exports file: ```
/                       192.168.1.100(rw,async,no_root_squash) 192.168.1.101(rw,async,no_root_squash) 192.168.1.110(rw,async,no_root_squash)
/home/scott/webmaster   192.168.1.1/24(rw,async)
/home/scott/bin         192.168.1.1/24(rw,async)
/media/EXTERNAL_HD      192.168.1.1/24(rw,sync,no_root_squash)
```Restart NFS: ```
sudo /etc/init.d/nfs-kernel-server restart
```Now, on the client, add entries to /etc/fstab. For example, ```
192.168.1.50:/home/scott/webmaster /home/scott/webmaster nfs rw,hard,intr 0 0
192.168.1.50:/media/EXTERNAL_HD    /media/external_hd    nfs rw,hard,intr 0 0
```**Make sure the mount point exists and is an empty directory!**

Now, issue ```
sudo mount -a
``` and you should be good to go--provided that your permissions problems are sorted out properly.

---

### Post by Quikee on 2007-05-16
> **Balinsky said:**
> 
But currently on the ssh side of things i almost have it working (i think)
i used sshfs [en.wikipedia.org/wiki/SSH_Filesystem]("http://en.wikipedia.org/wiki/SSH_Filesystem")
and mounted it at (on the laptop) /media/XHD

I thought i had it but when i navigate to it with nautilus i get
```
Couldn't display "/media/XHD".
The attempt to log in failed.

```


Don't use sshfs as "sudo" but as a normal user (better - mount it somewhere in home - it is using fuse so normal users can mount it without ). In sshfs other users (including root) don't have permission to view its mounted folder (you only see a file instead of a folder). 

to mount do:
"sshfs <user>@<host>:<remoteFolder> <localMountFolder>"
and to unmount: 
"fusermount -u <localMountFolder>"

There is no easier way to share folders between 2 linux computers especially as ssh is such a powerful tool that every linux machine just must have it. ;)

---

### Post by mssever on 2007-05-16
> **Quikee said:**
> There is no easier way to share folders between 2 linux computers especially as ssh is such a powerful tool that every linux machine just must have it. ;)

I've never gotten sshfs working through Nautilus, although I haven't tried really hard. My question, though, is whether the partition actually gets mounted in a way that's accessible from the command line or non-Gnome programs. Most of the other options in Nautilus' Connect to server dialog aren't real mounts.

---

### Post by Quikee on 2007-05-17
> **mssever said:**
> My question, though, is whether the partition actually gets mounted in a way that's accessible from the command line or non-Gnome programs. Most of the other options in Nautilus' Connect to server dialog aren't real mounts.

Yes. sshfs uses FUSE.. which works as "mount" in this respect, but allows also normal users to mount, not only root.

---

### Post by Balinsky on 2007-05-18
I actually got this all to work to my specifications (in the /media directory with permissions working)

i used fuse in fstab and got it working.

But the problem was that the speed of transfering data turned brutal on me
the 56Mbits/s of 802.11g just dont compare to the 480 Mbit/s of usb 2.0
so what happened was even though BT worked fine it was sluggish and turned my usually zippy laptop into something far less desireable.

so ill just have to settle to being tied down to my XHD (i know the *tragesty*)

thanks all
jebsky

ps ill post how i did it if anyone wants but i am on my other computer right now

---

