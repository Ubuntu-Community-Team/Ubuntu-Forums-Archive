---
title: "Help with Swap"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-24
I dont think ubuntu is using my swap partition.  I have a 2 GB one but i dont think its active. How do i activate it? I did "free-m" and this is what came up.
             
                  total       used       free     shared    buffers     cached
Mem:          2990       1308       1681          0         63        772
-/+ buffers/cache:        471       2518
Swap:            0          0          0

---

### Post by hunter99507 on 2010-12-24
From what i have been reading i think i deleted it from my fstab.  How do i fix that?

---

### Post by matt_symes on 2010-12-24
Hi

If Ubuntu doesn't need to use swap normally it does not use it. It does need it for hibernating though.

Have a look at swapon and swapoff. From the terminal type

```
man swapon
```

or 

[http://manpages.ubuntu.com/manpages//jaunty/en/man2/swapoff.2.html](http://manpages.ubuntu.com/manpages//jaunty/en/man2/swapoff.2.html)

Kind regards

---

### Post by matt_symes on 2010-12-24
Hi

> From what i have been reading i think i deleted it from my fstab. How do i fix that?

Post the output of (at the terminal)

```
sudo blkid
```

and 

```
cat /etc/fstab
```

Kind regards

---

### Post by hunter99507 on 2010-12-24
So i fixed it using "storage device manager" but i would like to know exactly what happened, that way in the future i could fix it with out using that program (Learning Experience).

watts@Ubuntu:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="88B46EC8B46EB7F8" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="7AE45774E457319D" TYPE="ntfs" 
/dev/sda4: UUID="948CFF808CFF5B66" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="68F3AA172703E1BC" TYPE="ntfs" 
/dev/sda6: UUID="a121933f-0815-495e-b51c-9950befea268" TYPE="ext4" 
/dev/sda7: UUID="695bb6bb-a133-4fd9-876a-862a0175e4a1" TYPE="swap" 
watts@Ubuntu:~$ cat /etc/fstab
/dev/sda5  /media/sda5  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda7  /media/sda7  swap  sw                                  0  0

---

### Post by matt_symes on 2010-12-24
Hi

> **hunter99507 said:**
> So i fixed it using "storage device manager" but i would like to know exactly what happened, that way in the future i could fix it with out using that program (Learning Experience).

watts@Ubuntu:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="88B46EC8B46EB7F8" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="7AE45774E457319D" TYPE="ntfs" 
/dev/sda4: UUID="948CFF808CFF5B66" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="68F3AA172703E1BC" TYPE="ntfs" 
/dev/sda6: UUID="a121933f-0815-495e-b51c-9950befea268" TYPE="ext4" 
/dev/sda7: UUID="695bb6bb-a133-4fd9-876a-862a0175e4a1" TYPE="swap" 
watts@Ubuntu:~$ cat /etc/fstab
/dev/sda5  /media/sda5  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda7  /media/sda7  swap  sw                                  0  0

I'm not 100% sure what happened, but i would advise you to use UUIDs in your fstab file and not device names as they can change if you meddle with your partitions. Did you change your partitions?

Kind regards

---

### Post by matt_symes on 2010-12-24
Hi

```
/dev/sda5 /media/sda5 ntfs nls=iso8859-1,users,umask=000,user 0 0 
/dev/sda7 /media/sda7 swap sw 0 0

```

Change your fstab to use UUIDs as below. Make sure you use your own UUIDs of course.

```
# / was on /dev/sda5 during installation
UUID=3d48429c-7361-4ab8-8689-54407673b141 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b1c6171a-075e-4291-af69-64baf751d10e none            swap    sw              0       0
```

What has happened to your root (/) mount?

This is not a wubi install is it? I don't know much about wubi.

Kind regards

---

### Post by hunter99507 on 2010-12-24
Ok ive been doing to reasearch and i think i got most of it. I do have 1 question though that i cant figure out. Right now i have my data drive automatically load on start up and i understand how to do that. What i cant do now is unmount that partition.

/dev/sda5  /media/sda5  ntfs    auto,user,exec,rw                 0  0  
/dev/sda7  /media/sda7  swap  sw                                       0  0  

It gives me and error message 

"umount: only root can unmount /dev/sda5 from /media/sda5"

How do i change it so anyone can mount and unmount, just not the root?

---

### Post by hunter99507 on 2010-12-24
Ok i changed the forth line from user to users. Now i can unmount but i cant mount.  How do i fix that?

/dev/sda5  /media/sda5  ntfs  auto,[COLOR=Red]users[/COLOR],exec,rw                  0  0  
/dev/sda7  /media/sda7  swap  sw                                       0  0  

When i click on the drive and try to mount it gives me this error.

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

---

### Post by hunter99507 on 2010-12-24
Hey also on a side note how do u do the "code" box in your posts?

---

### Post by hunter99507 on 2010-12-24
Sorry to answer your first question about the mount point /.  I am new at this and i deleted everything in the file because i though the storage manager messed it up.

---

### Post by matt_symes on 2010-12-24
Hi

Sorry for the delay. I have been busy. I will reply to all the posts starting off with the easiest first.

```
Hey also on a side note how do u do the "code" box in your posts?
```

When you write code or text in the message area highlight it and look on the tools panel just above the message area.

You will see a button that has # icon. Click that and it will wrap the hightlighted text in code tags.

Next to it, on the left, is the button for quote tags.

Kind regards

---

### Post by matt_symes on 2010-12-24
Hi

> **hunter99507 said:**
> Sorry to answer your first question about the mount point /.  I am new at this and i deleted everything in the file because i though the storage manager messed it up.

This is very serious and needs to be fixed right away. The root mount point needs to be specified in fstab.

Lets fix that now.

Kind regards

---

### Post by matt_symes on 2010-12-24
Hi

Right. Make a backup copy of your existing /etc/fstab file

Create a new one and add this inside it

```
UUID=a121933f-0815-495e-b51c-9950befea268 /  ext4    errors=remount-ro 0 1
UUID=68F3AA172703E1BC  /media/sda5 ntfs auto,users,exec,rw 0 0 
UUID=695bb6bb-a133-4fd9-876a-862a0175e4a1 none swap sw 0 0
```

Make sure you have a live CD ready (just in case) and reboot.

Kind regards

---

### Post by mcduck on 2010-12-24
> **hunter99507 said:**
> Ok ive been doing to reasearch and i think i got most of it. I do have 1 question though that i cant figure out. Right now i have my data drive automatically load on start up and i understand how to do that. What i cant do now is unmount that partition.

/dev/sda5  /media/sda5  ntfs    auto,user,exec,rw                 0  0  
/dev/sda7  /media/sda7  swap  sw                                       0  0  

It gives me and error message 

"umount: only root can unmount /dev/sda5 from /media/sda5"

How do i change it so anyone can mount and unmount, just not the root?
Change the "auto" to "noauto". Of course that means that it will not get automatically mounted on boot, but on the other hand normal users can mount & unmount it as they need to.

(you can't have it automount at boot and be unmountable by normal users at the same time, as it would get mounted by root user and normal users simply wouldn't have permissions to unmount it after that)

edit:
..and yes, definitely add the root partition back to fstab. Before you reboot the machine, or you'll have to fix this from a live-CD to get Ubuntu to boot at all...

---

### Post by hunter99507 on 2010-12-24
Everything has worked great! Below is my new fstab

```
UUID=a121933f-0815-495e-b51c-9950befea268  /  ext4  errors=remount-ro  0  1
UUID=68F3AA172703E1BC  /media/sda5  ntfs  auto,user,exec,rw  0  0
UUID="695bb6bb-a133-4fd9-876a-862a0175e4a1  none  swap  sw  0  0
```Also its weird that I didnt break ubuntu. I probably restarted my computer almost10 times with the ubuntu partition not mounted in fstab and everything seemed to work fine.  Was it supposed to break ubuntu? Did i get lucky? 

Below answered my question on why I cant mount and unmount.

> 
(you can't have it automount at boot and be unmountable by normal users  at the same time, as it would get mounted by root user and normal users  simply wouldn't have permissions to unmount it after that)I guess i just have one more question. In the original fstab ubuntu reads that code that I typed. Is that correct?  Also i noticed that i believe that there are notes in some "code" files but they are not read because they start with the "#" symbol. Correct?

Anyway I want to thank you matt_symes and mcduck for helping me with my issues and making this a learning experience.

---

### Post by matt_symes on 2010-12-24
Hi

> I guess i just have one more question. In the original fstab ubuntu reads that code that I typed. Is that correct?

Yes

> Also i noticed that i believe that there are notes in some "code" files but they are not read because they start with the "#" symbol. Correct?

Yes, but they are called comments.

Can you mark the thread as solved.

Kind regards.

---

