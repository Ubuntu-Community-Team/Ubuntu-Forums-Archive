---
title: "Recovery Reinstall, Preserving User Info"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by djmoore on 2009-03-10
I have lost my /var and /tmp directories, due to a hardware problem (and, I confess, inadequate backup). It appears I need to reinstall Ubuntu to recover from that.

Please, what must I do to reinstall Ubuntu, and preserve user account and security information (such as the passwd file)? I am perfectly willing to reinstall all my applications, I don't have many. 

I've searched the forums and the web for a procedure to do this, but get swamped by returns for general installation procedures and locking down on security for installed systems.

Ideally, I would boot from my Hardy Heron CD, download Intrepid, and install from the image on the hard drive (this would be a separate drive from the one where I will install). On the other hand, installing Heron and then upgrading isn't that onerous.

===

I am able to log on to a blank orange screen (no desktop), then press ctrl-alt-F1 to get a terminal. 

From there, here's the output of mount (stripped of non-hard-drive goo and dribble):
```

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb1 on /boot type ext3 (rw,relatime)
/dev/sdb4 on /home type ext3 (rw,relatime)
/dev/sdb6 on /mnt type ext3 (rw,relatime)
/dev/sdb7 on /usr type ext3 (rw,relatime)
/dev/sda1 on /var type ext2 (rw,relatime)
/dev/sda3 on /tmp type ext2 (rw,relatime)
/dev/sda2 on /data type ext3 (rw)

```
There's also a swap file on /dev/hda2. 

Finally, I manually mounted /dev/sda2 for this list, but it normally mounts automatically as /home/public, and I don't know why or how. Something I did, I'm sure, but darned if I know what. It's not in /etc/fstab, either:
```

# /dev/sdb6   20 GB / 150 GB
UUID=2bec7c8a-b5c0-4b78-b628-35cc8b5663de /               ext3    relatime,errors=remount-ro 0       1

# /dev/sdb1   94 MB / 150 GB
UUID=dba83e88-3b9c-4d66-96b2-e54b26fc2474 /boot           ext3    relatime        0       2

# /dev/sdb4  105 GB / 150 GB
UUID=59654dd5-60eb-4a30-a883-e7125c40e3ba /home           ext3    relatime        0       2

# /dev/sdb7    7 MB / 150 GB
UUID=0bd59e73-c809-49a3-bbbe-c57d3afbffb1 /mnt            ext3    relatime        0       2

# /dev/sdb8   20 GB / 150 GB
UUID=98fbc0df-5aa1-4f3c-84e4-862f78c7dd01 /usr            ext3    relatime        0       2

# /dev/sdb2    2 GB / 150 GB
UUID=d10aa764-130e-489a-91c8-4a2e86a68a7c none            swap    sw              0       0

# /dev/sda1    4 GB / 500 GB
UUID=1982873f-137f-49c6-9b6a-1b76ad050085 /var            ext2    relatime        0       2

# /dev/sda3    1 GB / 500 GB
UUID=1451af4e-7359-4026-8472-c610e02579ad /tmp            ext2    relatime        0       2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8    0       0
/dev/fd0        /media/floppy0  auto        rw,user,noauto,exec,utf8 0       0

```
No, I don't understand why mount says the / folder is on /dev/sdb5, but fstab says it should be  on sdb6.

If there's a way to re-create /var and /tmp without re-installing, that would be nice too, but I'd really like to find a good re-install procedure.

---

### Post by wolfen69 on 2009-03-10
the simple way would be to just copy your home directory (via live cd) and then replace it after you reinstall ubuntu. i think you made it more complicated than you needed to from the beginning. 

most hard core users don't even make that many partitions. /, home, and swap is all you really need.

i just make 1 big partition besides swap and then occasionally backup what hidden config files i want from the home folder. simple and efficient.

---

### Post by philinux on 2009-03-10
In the old days those partitions would be useful but now /, swap and /home is all thats needed.

---

### Post by djmoore on 2009-03-10
*sob* I spent hours researching partitioning schemes. But OK. 

But just preserving the home directory will also preserve all the permissions and stuff through a re-install?

---

### Post by louieb on 2009-03-10
Just a couple of things. the comments in fstab could be wrong. really need to check the UUID. to list use the ```
sudo blkid
``` command. I would trust the mount command output.

When you reinstall two things. 1) Be sure to use the same user name and if you have more than one user be sure to add then back in the same order.   Linux uses the user name sometimes and other times it uses the user ID (a four diget number) 1st user added has an id of 1000.  2) when you get to the partition part of the install just make sure the format check box for your home partition is not checked. 

Good luck.

---

### Post by djmoore on 2009-03-10
> **louieb said:**
> really need to check the UUID. to list use the blkid command. OK, thanks.

> When you reinstall two things. 1) Be sure to use the same user name and if you have more than one user be sure to add then back in the same order.  !!!

I only have root and two users; fortunately I think I remember which one went in first.

But what if I had a thousand users? Is there really no way to back up the permissions and passwords databases?

> 2) when you get to the partition part of the install just make sure the format check box for your home partition is not checked. Thanks. I appreciate everyone's help.

---

### Post by djmoore on 2009-03-12
OK, I've repartitioned my 150 GB IDE drive with / and swap partitions only, and moved /home to my 500 GB SATA drive.

But please, one last double check here before I press the DO IT button:
> **louieb said:**
> 2) when you get to the partition part of the install just make sure the format check box for your home partition is not checked.I can tell the 7.10 LiveCD Installation utility partition section to mount the SATA at /home, keeping the Partition option **un**checked, and the current contents of /home (my life, such as it is) will **not** be disturbed, correct? But it will be established as the default /home folder, so that when I add my everyday username, it will just pick up the existing /home/username folder, without disturbing the existing contents?

Do I have it right?

(Yes, I'm backing it up, darn betcha. But I'm using the flaky drive that is the reason for this exercise to do it, because the drive in my external backup bay won't spin up, and it's been used about five times. Both Seagates. All Western Digital now, darn betcha.)

Thanks again for the help so far.

---

### Post by louieb on 2009-03-12
Thats how I do it when instead of upgrading to the new version I do an install.  Just remember don't format /home  and match user name and id when adding your other users. 

Btw if they are still around look in  **/etc/passwd  **or **/etc/group** to find the user id for a given user.  
Good luck.

---

