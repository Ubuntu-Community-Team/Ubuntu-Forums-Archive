---
title: "Missing Home Directory"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-05-03
I have a separate home partition. When I first installed 8.10 I created one account and mounted the home directory to the partition. Everything worked fine for a while. The only small problem I had was when I logged in, I would get an error about the .dmrc. I'm sorry I don't remember exactly what the error message said. I then used:

chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority

I did this three times. One for each account I had on the old home directory. 

I messesd up typing a couple of times because I put a space after the "." and before the "dmrc" I also forgot to type "/home/" a couple times. 

Now I when I try and log in to the first account, I get a message about how it couldn't update the ICEauthority. I then get a message saying how it can't load the graphical interface. All I get is a black screen. I can still log into the other accounts, just not the one I first mounted when I was installing 8.10.

 When I check the home folder (using the live cd), it says that the home folder is empty. It's empty even after I show the hidden files. I don't have any files show up when I look through my home folder. 

I don't think that files have been erased. The partition has 56GB of total space and when I check it, it says that only 22GB is free, which is around the same amount I had left before this problem.

What do I need to do to get my home directory back?


Please let me know if you need any more info.

---

### Post by jerrrys on 2009-05-03
can't help you with your problem, but maybe if you can use a more descriptive title, that would help....people tend to skip over things like "Huuuuugggge problem!!!!!!!!!!!"

---

### Post by spiderbatdad on 2009-05-03
are you sure you are seeing your /home from the livecd and not the /home on the livecd?
From the live cd```
sudo mount /dev/sda1 /mnt
ls -al /mnt/home/username
```/dev/sda1 assumes Ubuntu is the only os on the disk. Check first ```
fdisk -l
```to find sdaX.
Check the permissions of /home/username. From the command above. Also check ownership. Default permissions are 755 or rwxr-xr-x. ```
cd /mnt/home/username
ls -al
```to see your files.

---

### Post by Sup3r3g0 on 2009-05-03
> **jerrrys said:**
> can't help you with your problem, but maybe if you can use a more descriptive title, that would help....people tend to skip over things like "Huuuuugggge problem!!!!!!!!!!!"

I'll fix it. Thanks for the advice.

---

### Post by Sup3r3g0 on 2009-05-03
Okay, I'm able to see the files in the terminal now. I did a 

```

sudo su

cd ///media/disk/username
ls -al

```

Now, what do I do so I can see my files in Nautilis? I clicked on my home folder properties and it says that there's nothing in my home folder.

---

### Post by Sup3r3g0 on 2009-05-03
[Old Thread]("http://ubuntuforums.org/showthread.php?t=1147603")

> **Sup3r3g0 said:**
> I have a separate home partition. When I first installed 8.10 I created one account and mounted the home directory to the partition. Everything worked fine for a while. The only small problem I had was when I logged in, I would get an error about the .dmrc. I'm sorry I don't remember exactly what the error message said. I then used:

chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority

I did this three times. One for each account I had on the old home directory. 

I messesd up typing a couple of times because I put a space after the "." and before the "dmrc" I also forgot to type "/home/" a couple times. 

Now I when I try and log in to the first account, I get a message about how it couldn't update the ICEauthority. I then get a message saying how it can't load the graphical interface. All I get is a black screen. I can still log into the other accounts, just not the one I first mounted when I was installing 8.10.

 When I check the home folder (using the live cd), it says that the home folder is empty. It's empty even after I show the hidden files. I don't have any files show up when I look through my home folder. 

I don't think that files have been erased. The partition has 56GB of total space and when I check it, it says that only 22GB is free, which is around the same amount I had left before this problem.

What do I need to do to get my home directory back?


Please let me know if you need any more info.



> **spiderbatdad said:**
> are you sure you are seeing your /home from the livecd and not the /home on the livecd?
From the live cd```
sudo mount /dev/sda1 /mnt
ls -al /mnt/home/username
```/dev/sda1 assumes Ubuntu is the only os on the disk. Check first ```
fdisk -l
```to find sdaX.
Check the permissions of /home/username. From the command above. Also check ownership. Default permissions are 755 or rwxr-xr-x. ```
cd /mnt/home/username
ls -al
```to see your files.

---

### Post by Sup3r3g0 on 2009-05-03
Here's what I did:

```

sudo su

cd ///media/disk/timothycbautista
ls -al

```

Now I can see all of my files in the terminal. What do I need to so I can see the files when I click on the folder? How do I set the default permissions?

---

### Post by Sup3r3g0 on 2009-05-03
Alot of my stuff has "drwxr-xr-x " in the first column. How do I change that to "rwxr-xr-x?" And is this what I should do?

---

### Post by Volt9000 on 2009-05-03
> **Sup3r3g0 said:**
> Alot of my stuff has "drwxr-xr-x " in the first column. How do I change that to "rwxr-xr-x?" And is this what I should do?

You can't remove the "d" at the beginning, since that is not a permission-- that prefix denotes a directory.

I'm not sure I quite understand what you're trying to do...

---

### Post by Sup3r3g0 on 2009-05-04
Oh, I thought that I had to try and change it to rwxr-xr-x because spiderbatdad mentioned how it was the default.

I'm trying to make it so I can actually see the files in my home folder. Right now, I can only see the files if I use the terminal from the Live CD. Without the live CD, when I try and log in, all I get is a black screen. If I go the home directory and click and the folder, all of my files are using. Right clicking and checking the folder properties says that I have nothing in the folder. But when I navigate to the folder using the terminal from the Live CD, I can see the files. I know that the files are still there because, something is taking up around 25GB of space, the same around of space that my home folder took up. 

The home folder is on a separate partition. When I first installed, I selected the partition as the mount point for my home directory. 

Thanks for the help so far.

---

### Post by Sup3r3g0 on 2009-05-04
I tried logging in again. I get these messages:

```

couldn't update the file /home/timothycbautista/.ICEauthority

problem witht he configuration server
(usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

```

This is in addition to message about the .dmrc file and how the home directory is being ignored.

---

### Post by spiderbatdad on 2009-05-04
ok check the permissions on ///media/disk/etc/gconf/gconf.xml.system
```
ls -al ///media/disk/etc/gconf/gconf.xml.system
```The permissions should be 755, that is rwxr-xr-x.
to change ```
sudo chmod 755 ///media/disk/etc/gconf/gconf.xml.system
```

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

---

### Post by Volt9000 on 2009-05-04
> **spiderbatdad said:**
> ok check the permissions on ///media/disk/etc/gconf/gconf.xml.system
```
ls -al ///media/disk/etc/gconf/gconf.xml.system
```The permissions should be 755, that is rwxr-xr-x.
to change ```
sudo chmod 755 ///media/disk/etc/gconf/gconf.xml.system
```

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

Ok I gotta ask-- what's with the triple slashes? If you're specifying an absolute path you only need one slash at the front.

---

### Post by Sup3r3g0 on 2009-05-04
> **spiderbatdad said:**
> ok check the permissions on ///media/disk/etc/gconf/gconf.xml.system
```
ls -al ///media/disk/etc/gconf/gconf.xml.system
```The permissions should be 755, that is rwxr-xr-x.
to change ```
sudo chmod 755 ///media/disk/etc/gconf/gconf.xml.system
```

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

Thanks, I'll try it out when I get back home.

> **Volt9000 said:**
> Ok I gotta ask-- what's with the triple slashes? If you're specifying an absolute path you only need one slash at the front.

Yeah I realized that eventually. Thanks

---

### Post by Sup3r3g0 on 2009-05-04
```

root@ubuntu:~# ls -al ///media/disk/etc/gconf/gconf.xml.system
ls: cannot access ///media/disk/etc/gconf/gconf.xml.system: No such file or directory

```

---

### Post by Sup3r3g0 on 2009-05-04
I got it!

```

root@slackware:~# chmod -R 755 /home/timothycbautista

```

Thanks everybody for all the help!

---

