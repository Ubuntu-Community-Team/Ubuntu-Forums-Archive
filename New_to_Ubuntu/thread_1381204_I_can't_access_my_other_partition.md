---
title: "I can't access my other partition?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-14
I did the side-by-side installation of Ubuntu on my 250gb hard drive and gave it 15gb or so for the system files and the swap.  Now I'm trying to delete stuff from the other partition (while in Ubuntu) an it's saying I don't have the permission to do so.

Any ideas? :)

---

### Post by audiomick on 2010-01-14
what is the other partition? Is it a windows install? a data partition?
What is the file system? ntfs or ext3 or ext4 or something else?
What are you trying to delete?

---

### Post by Dreakon on 2010-01-14
It's a windows install, it's a NTFS file system and I'm trying to delete some useless game RAR files I had on there that are taking up space.

I could go into Windows and do it, but honestly, I'm trying to phase windows out and eventually just turn it into a simple data partition (delete everything windows related off of it and just keep it for game installations, music, videos, etc).  Is that possible or am I going about this the wrong way?

---

### Post by audiomick on 2010-01-14
I would have thought that would work.
You could try opening the file manager with
```
gksu nautilus
```
to give yourself root privileges, but I am not convinced that this would make a difference, as ntfs partitions don't implement linux permissions.

Generally, as far as I know, other partitions like the windows partition should be mounted such that you can read from and right to them.

Anyway, give it a go. Might work..

---

### Post by Dreakon on 2010-01-14
I used that command in Terminal and it brought up the file browser it seems.  Still couldn't delete anything.

It brought up a bunch of warningy type things though as it started and as I was navigating...

```
** (nautilus:3583): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3583): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3583): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:3583): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:3583): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:3583): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

```

Could any of that be causing the problem?

---

### Post by audiomick on 2010-01-14
Yes, starting nautilus with "gksu" does generate some error messages. Mine says
```
mick@ubuntu-desktop:~$ gksu nautilus
Initializing nautilus-gdu extension

** (nautilus:2551): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2551): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2551): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-image-converter extension


```

If you still can't delete, it might be easier just to do the cleaning out in windows than to try and find out what is stopping you.

---

### Post by J V on 2010-01-14
better yet, format :P

---

### Post by Dreakon on 2010-01-14
My goal is to get rid of Windows on the other partition.  This means keeping all of my games, software, music, documents and videos intact and simply deleting any Windows related files.  The benefit of course being then I could switch back to Windows, update Ubuntu, try other O/S's safely with minimal risk of effecting those files.  This is more convenient and is what is leading me to my decision to try and simply delete Windows related files rather than completely format the partition.

It's not fun to try and move the 200 or so GB worth of files to my other computer as backup lol.  So reasonably, I'd like to try and solve why this other partition is being a silly goose before I go backing everything up and formatting it. :P

Oh, and I can't clean out the Windows files while I'm in Windows.  At some point I'll have to get this working unless I opt to format... ;)

---

### Post by J V on 2010-01-14
Not quite gonna work that way...

Reinstalling windows will format the partition anyway, and it will try to do the same with your linux partitions if its any kind of reliable :P

if you have them on the same network you can samba all the stuff over at once (no hussling usb sticks)

so yeah, samba your 200 gigs, should take less than 24 hours, linux can easily handle that ;)

then wipe the win partition... Only option I can see...

---

### Post by Dreakon on 2010-01-14
> **J V said:**
> Reinstalling windows will format the partition anyway
It'll format the partition I'm not installing it on? :(

---

### Post by J V on 2010-01-14
Windows doesn't like other OSs, especially linux... it has in some cases gone out of its way to *target* peoples /homes :P

but yeah, installing it will be dangerous as hell, and if you dont back your stuff up you might as well format anyway ;)

could you show us your partitioning scheme so I get an idea of how its layed out? (sudo fdisk -l)

---

### Post by Dreakon on 2010-01-14
> **J V said:**
> could you show us your partitioning scheme so I get an idea of how its layed out? (sudo fdisk -l)
```
/dev/sda1   *           1       28457   228580821    7  HPFS/NTFS
/dev/sda2           28458       30401    15615180    5  Extended
/dev/sda5           28458       30314    14916321   83  Linux
/dev/sda6           30315       30401      698796   82  Linux swap / Solaris
```

The first one is the one with Windows and all of my files, the rest is space dedicated to Linux and the swap partition.

---

