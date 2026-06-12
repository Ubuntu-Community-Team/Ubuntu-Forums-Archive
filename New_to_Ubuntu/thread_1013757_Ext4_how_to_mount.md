---
title: "Ext4 how to mount?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by rybaxs on 2008-12-17
Help please... my Feisty OS file system was change into ext4 after using super grub disk.

---

### Post by lametike on 2008-12-17
ext 4??i though the newest is ext3?

---

### Post by rybaxs on 2008-12-17
Cannot mount drive
> 
The volume uses the ext4 file system which is not supported by your system.


---

### Post by Elfy on 2008-12-17
ext4 is about but not default afaik

how did supergrub change the filetype - what did you do?

Do you know that feisty is out of support now?

---

### Post by rybaxs on 2008-12-17
Sorry, I didn't know how it happened because other administrator was the one who change the ext3 to ext4, then the live OS, other OS detect that the drive was now change to ext4...

is there any other way I can retrieved my server files?

---

### Post by Elfy on 2008-12-17
I'm not sure - ext4 is recognised by later versions. I know you can use it in hardy.

Can you not find out from the other admin what was done.

You might be able to retrieve them from a livecd - but again not sure.

---

### Post by rybaxs on 2008-12-17
I can't retrieve them in a live CD, I'm looking for thread of ext4 like this [http://www.uluga.ubuntuforums.org/showthread.php?t=992713](http://www.uluga.ubuntuforums.org/showthread.php?t=992713)..

I was thinking if i will try the Ubuntu 9.04, it will work? I'm not sure with this. :(

---

### Post by rybaxs on 2008-12-17
Helpful links

[http://ubuntuforums.org/archive/index.php/t-837589.html]("http://ubuntuforums.org/archive/index.php/t-837589.html")

[http://ubuntuforums.org/showthread.php?t=837589]("http://ubuntuforums.org/showthread.php?t=837589")

[http://brainstorm.ubuntu.com/idea/4468/]("http://brainstorm.ubuntu.com/idea/4468/")

[http://ubuntuforums.org/showthread.php?t=846655http://ubuntuforums.org/showthread.php?t=837589]("http://ubuntuforums.org/showthread.php?t=846655http://ubuntuforums.org/showthread.php?t=837589")

---

### Post by Elfy on 2008-12-18
Have you not found out what was changed?
> 
Also ext4 is backwards and forwards compatible. So you could just mount as ext3 or ext2 and access it in _that_ mode, or use ext4. 

If this is the case then it would suggest that you can mount them as ext3 which feisty will recognise. I hesitate to say do it until you have some idea what was done in the first place.

I wouldn't though be installing a dev version on a server, if you went for hardy 8.04 then it is a LTS and as such supported for longer.

If it is possible to mount as ext3 then that could be accomplished with fstab I expect.

Find out from this other admin what was done and then we can move on hopefully.

---

### Post by rybaxs on 2008-12-18
the last action that was made is ```
$sudo apt-get install gnome
```
on Feisty OS. then at the GRUB error2 occur, I installed the super grub disk to boot the disk, but the super grub disk didn't do nothing, so I try to rescue broken OS by using the Ubuntu server disk, but the rescuer can't recognize the sda1,2,3~.. so my next step is to run jaunty live and access the hard disk..

Hi forestpixie,
How can I mount ext4 to ext3?

---

### Post by Elfy on 2008-12-18
I'm not sure - boot the livecd and see if it recognises the drives first, but I have to ask why you're looking at a development version for a server.

I would personally be looking at Hardy for a server.

Once you've booted the livecd see if you can access the drives, if it does check what fstab is saying in there.

In the meantime can you post your current fstab please

```
cat /etc/fstab
```

---

### Post by rybaxs on 2008-12-18
> **forestpixie said:**
> I'm not sure - boot the livecd and see if it recognises the drives first, but I have to ask why you're looking at a development version for a server.

I would personally be looking at Hardy for a server.

Once you've booted the livecd see if you can access the drives, if it does check what fstab is saying in there.

In the meantime can you post your current fstab please

```
cat /etc/fstab
```


```

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```
This is the result,

When I open the disk this is the error message
> 
Cannot mount volume
The volume uses the ext4file system which is not supported by your system.

> 
Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply:Did
not receive a reply. Possible causes include: the
remote application did not send a reply, the message
bus security policy the reply, the reply timeout
expired, or the network connection was broken.


Disk Properties
Type: unknown type
Size: unknown
Volume: uknown
MIME Type: application/octet-stream
Modified: unknown
Accessed: unknown

---

### Post by Elfy on 2008-12-18
That's the livecd fstab, I meant the system fstab.

I have really no idea whether it is as simple as changing the filetype in fstab.

You're post #10 doesn't really answer > Find out from this other admin what was done and then we can move on hopefully.

Perhaps you can dig a bit deeper into the bash history or get the other admin to post something.

In the meantime I've flagged the thread on the UA team's site maybe someone there knows something.

I assume that if the situation is irretrievable that you have good backups it being a server.

---

### Post by Locke_99GS on 2008-12-18
GRUB doesn't support, and won't boot to ext4 partitions. (yet) If the whatever partition /boot resides on was changed to ext4, it won't boot with GRUB. Create a seperate ext3 partition to mount at /boot, then install (or copy?) /boot.

Downlaod the current LiveCD with a bootable PC or OS, burn it, and boot it. (any LiveCD will work, *buntu, Fedora, whatever) The ext4 drive can be mounted as ext3, and you will be able to access it that way.

Alternatively, once in a livecd environment, you may (?) be able to use *tune2fs* to change the filesystem back to ext3.

---

### Post by rybaxs on 2008-12-18
hello forestpixie

this is what actually happened ..
from the last part of the system log..
someone made the mistake at the terminal using root
```
$mv
```
all system files was move to one sub folder, then at the boot
GRUB error15.. so i move the system files back to /
after moving the files and folders, it boots up the OS,
but you cannot login because the system is read only.
so i chown to root:root
after this the other sys ad try to get in in the gnome..
our server OS is Ubuntu Feisty - after the other SysAd get in
he tries to update the gnome, after the downloading of package,
the system hangs up and restarted.. and in the GRUB error2 occur, 
so i mount the disk to other Ubuntu 8.04 the disk cannot be read because
it shows that it is ext4..

sorry for the reply forestpixie, thank you so much for the time.. i realy really appreciate it.

I try the jaunty but it seems it is not working.. :( i try looking for the specs..

---

### Post by Elfy on 2008-12-19
Try this boot the 8.04 livecd

Open terminal and 

```
sudo mkdir /mnt/test
```

After running sudo fdisk -l - use the information you get to replace  /dev/sxy for one of your drives and see if we can mount it as ext3

```
sudo mount -t ext3 /dev/sxy /mnt/test
```

---

