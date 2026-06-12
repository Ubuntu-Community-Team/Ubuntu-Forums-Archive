---
title: "Unmounting &amp; potential data loss?"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by M1ke on 2010-01-20
I've been idly browsing a site about Linux's directory structure ([http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)) and came across this line regarding partition mounting:
 
> **</lost+found>**
Here Linux keeps the files that it restores after a system crash *or when a partition hasn't been unmounted before a system shutdown.* This way you can recover files that would otherwise have been lost.
 
Now, as a long-time Windows user I'm still wrapping my head around the concept of mount points, mounting and unmounting etc. Under my current system setup most of my data is still stored within Windows' partition, which I tend to mount when I log on to Ubuntu so that I can get to my media, music, photos and so on. But ordinarily I don't bother to unmount the partition again before I shutdown - is this a bad thing? It never occurred to me that there was even potential for harm here!

---

### Post by lotharmat on 2010-01-20
AFAIK; Ubuntu, when shutdown correctly will auto dismount any mounts

So nothing to worry about!

---

### Post by ajgreeny on 2010-01-20
> **lotharmat said:**
> AFAIK; Ubuntu, when shutdown correctly will auto dismount any mounts

So nothing to worry about!
This answer is spot-on correct.  The problem is not generally with internal hard drives, but external usb drives, which many people using windows simply pull out, not using the "safely remove" option on the task bar.  That can cause problems even in windows if you are still writing to the usb drive, but still most people seem to not bother with the potential problems it could cause.

In linux OSs, if you just remove a still mounted ntfs drive, it will not be possible to mount it again next time without the force option being used, as the filesystem will have been marked as "locked" and in use by linux and therefore no activities can happen to it until it has been "unlocked".

Save yourself the problem by always unmounting usb drives before you remove them from the socket.

---

### Post by M1ke on 2010-01-20
> **ajgreeny said:**
> Save yourself the problem by always unmounting usb drives before you remove them from the socket.
 
Actually that's another thing I meant to ask - I also have an external USB drive that tends to just stay plugged in most of the time. Will that be auto-unmounted at shutdown too, or is there any distinction made between internal and USB-plugged drives? I noticed it auto-mounts on login, unlike my Windows partition.

---

### Post by muteXe on 2010-01-20
google "fstab" and "mtab".
I'd have thought your windows partition would have been auto-mounted on boot up though. Weird.

---

### Post by audiomick on 2010-01-20
As far as I know, as long as the computer is able to shut down properly, you don't have to worry. It turns off the lights and puts the cat out before it goes to bed.;)

---

### Post by John Bean on 2010-01-20
> **M1ke said:**
> I also have an external USB drive that tends to just stay plugged in most of the time. Will that be auto-unmounted at shutdown too

Yes. By default removable storage devices are auto-mounted by fuse, fixed disks are handled using the entries in fstab. But once mounted they are treated the same at shutdown.

---

### Post by ajgreeny on 2010-01-20
> **muteXe said:**
> google "fstab" and "mtab".
I'd have thought your windows partition would have been auto-mounted on boot up though. Weird.
No, your windows partition will only mount at boot time if you tell it to in /etc/fstab by manually editing that file, or you use ntfs-config to configure the way ntfs-3g works.

If you want a quick way to mount disks have a look at the disk-mounter panel applet; it's very useful if you have a lot of disks/partitions and don't wish to mount everything at bootup.

---

### Post by M1ke on 2010-01-20
All good to know, thanks very much for the helpful replies, everyone!

---

### Post by hectorbls on 2010-07-08
I just wanted to know if the same auto-unmount principal applies when you log off. if it doesn't, is there something, perhaps a script, that will unmount all volumes (internal and external) at the log off?

---

