---
title: "I do not own my home folder!!"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by beegary on 2010-01-02
I was having some problems with starting programs:
[http://ubuntuforums.org/showthread.php?t=1370737](http://ubuntuforums.org/showthread.php?t=1370737)

Now \i realise it is down to root owning my home directory.
My home is /home/bee
which is a windows share, mounted directory from fstab:
```
/dev/sda3 /home/bee ntfs-3g defaults,locale=en_GB.UTF-8 0
```

I cant seem to be able to chown my home directory? Im totally stuck!!!

---

### Post by CharlesA on 2010-01-02
Are you able to verify that it's mounted and that /home/bee is owned by root?

If it is, then running *sudo chown -R user:user /home/bee* should fix the problem.

---

### Post by Methuselah on 2010-01-02
Sorry, I don't know much about using ntfs as a linux home folder.
I'm guessing there might be some caveats there although I also have heard ntfs support is very stable.
Since my machine is strictly linux and has no ntfs formatted disks I have no experience here.

It might still be worth itfor you to know the permissions of your home folder.

```

ls -dl /home/bee

```

If by chance you're the owner but for some reason the owner doesn't have rwx.
The above command will tell who the owner and group are as well as the permission bits.

---

### Post by beegary on 2010-01-02
> Are you able to verify that it's mounted and that /home/bee is owned by root?
In nautilus i can explore to the directory and it has all my files from the mount. I right click it and select permissions which says the owner is root


> If it is, then running *sudo chown -R user:user /home/bee* should fix the problem.
I ran this command and got the following:
```
bee@ubuntu:~$ sudo chown -R bee:bee /home/bee
chown: cannot access `/home/bee/.gvfs': Permission denied
```

......And /home/bee is still owned by root??

---

### Post by beegary on 2010-01-02
> **Methuselah said:**
> 
```

ls -dl /home/bee

```If by chance you're the owner but for some reason the owner doesn't have rwx.
The above command will tell who the owner and group are as well as the permission bits.

Here is the results of that command:
```
bee@ubuntu:~$ ls -dl /home/bee
drwxrwxrwx 1 root root 24576 2010-01-02 22:17 /home/bee
```

---

### Post by Cheesemill on 2010-01-02
I'm pretty sure you'll end up with alot of unsolvable problems trying to use a samba share as your home folder. Your home folder needs specific permissions on it to work properly which aren't underdstood by samba.

---

### Post by Paqman on 2010-01-02
> **beegary said:**
> 
I cant seem to be able to chown my home directory? Im totally stuck!!!

The reason is that it's root that mounts things in fstab. If you change your fstab line so that it mounts /home instead of /home/bee then you might have more luck.

However, NTFS can't handle permissions, so i'm not sure if you're going to be able to set them anyway.

---

### Post by Buuntu on 2010-01-02
From: [http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727)

> 
```
sudo chown username /home/username 
```

[COLOR=DarkRed]Note 2[/COLOR]: I did not use the recursive *-R* switch. While all folders and files within the $HOME folder normally are owned by the user, the only folder which needs to have the ownership changed to eliminate this error is the $HOME folder itself. You may run this command as "sudo chown -R username:username /home/username" if you want to ensure the entire contents of your home folder belong to you and your usergroup.

[COLOR=DarkRed]Note 3[/COLOR]: When this command is run you may get a message stating "*unable to access /home/user/.gvfs.*. This is not a problem and references the .gvfs is a virtual file system. The command should do what is necessary to fix the problem, but you can avoid this message by accomplishing these commands first.
     ```
umount /home/[username]/.gvfs
rm -r /home/[username]/.gvfs 
```
*[COLOR=Navy]**and must not be writable by others**[/COLOR]*:
     ```
chmod 755 /home/username 
Other acceptable permissions include 750 or 700.

```
Log out and back in for the changes to take effect. Rebooting is not necessary.

---

### Post by beegary on 2010-01-02
> **Cheesemill said:**
> I'm pretty sure you'll end up with alot of unsolvable problems trying to use a samba share as your home folder. Your home folder needs specific permissions on it to work properly which aren't underdstood by samba.

I am a total newb but i thought i wasnt using samba but an ntfs mount instead?or are they really the same thing?
Either way it looks like ive bricked my installation!!!

---

### Post by J V on 2010-01-02
You havent bricked your instalation, you aren't a complete newb, and you are using an ntfs mount (which you probably shoulden't) which isn't samba

---

### Post by pmooney78 on 2010-01-02
I've tried this same situation and figured out a couple of things that might be helpful.

First: The ideal solution is to put your home folder on a native Linux-type filesystem. I prefer ext3, but other people have other preferences.

The real problem is that Windows drives don't support Linux-style ownership and permissions. You can't chown, chgrp, or chmod anything on a Windows partition because NTFS doesn't support those features.

Your best option, besides moving your home folder to a Linux filesystem, might be to set the options in /etc/fstab for the WHOLE VOLUME that contains the home folder you want to use ... you can set the user ID and/or group ID that is used for the whole volume in that configuration file, and that might result in you owning your home folder again.

Think about why it is that you really want to put your home folder on a Windows share and whether you can accomplish those same ends while still keeping your home partition on a Linux filesystem. It'll be less trouble in the long run, I suspect.

---

### Post by Cheesemill on 2010-01-02
> **beegary said:**
> I am a total newb but i thought i wasnt using samba but an ntfs mount instead?or are they really the same thing?
Either way it looks like ive bricked my installation!!!


Sorry, I meant ntfs not samba (trying to do to many things at once at the moment).

Using an NTFS partition as /home is really not recomended.
Why exactly did you try this? There may be better ways to achieve what you were after.

---

### Post by beegary on 2010-01-02
> **Buuntu said:**
> From: [http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727)

Thanks buuntu but i have followed those instructions with no luck. 
I think this may be the time for me to forget dual booting and windows, and trying to share my home directory between both installations!!!!
The time was gonna come at some point!!!

---

### Post by beegary on 2010-01-02
> **Cheesemill said:**
> Sorry, I meant ntfs not samba (trying to do to many things at once at the moment).

Using an NTFS partition as /home is really not recomended.
Why exactly did you try this? There may be better ways to achieve what you were after.

I have a dual boot with XP. in windows i have always had a separate partition for My Documents, and wanted the same thing in Ubuntu.
So in my current setup the Ubuntu /home and XP ~/My Documents are the same location.


I think I may just remove the ntfs and xp partition and forget about these issues!!!!!

---

### Post by Cheesemill on 2010-01-02
> **beegary said:**
> Thanks buuntu but i have followed those instructions with no luck. 
I think this may be the time for me to forget dual booting and windows, and trying to share my home directory between both installations!!!!
The time was gonna come at some point!!!

There's no need to share your entire home folder between installations. If it's just stuff like music and videos you want to use on both installs then you can have Ubuntu set up as it's meant to be (with /home on an ext partition) and symlink folders from your Windows installation into it.

For example on one of my machines my Music and Video folders in Ubuntu are actually symlinked to the My Music and My Videos folders on my Windows drive. It's only having configuration files on an NTFS partition that upsets Ubuntu.

---

### Post by J V on 2010-01-02
if you use a seperate partition alltogether for your /home (its really a whole different beast than your "my documents") and install aditional drivers on windows, you can access eachothers partitions (yes, windows will read ext)

---

### Post by beegary on 2010-01-02
Thanks everyone for all your help, I didnt realise what /home is used for.
Steep Ubuntu/linux learning curve but I am enjoying it.

Is there anything I should watch out for when removing my Windows partition/boot?

> **pmooney78 said:**
> I've tried this same situation and figured out a couple of things that might be helpful.
First: The ideal solution is to put your home folder on a native Linux-type filesystem. I prefer ext3, but other people have other preferences.


I| didnt realise there was more than 1 filesystem in linux, ill go a read up about that before rejigging my partitions in gparted.

> **Cheesemill said:**
> 
For example on one of my machines my Music and Video folders in Ubuntu are actually symlinked to the My Music and My Videos folders on my Windows drive. It's only having configuration files on an NTFS partition that upsets Ubuntu.

So if i was removing my windows partition altogether is this the best way of having important data/network shares on a separate partition? via symbolic links? Or is there a better way to achieve it in a Ubuntu only setup?

---

