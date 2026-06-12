---
title: "WoW on an external drive"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by cawnc4 on 2011-06-03
Hey this is my first post on this forum, I have been using ubuntu off and on since 8.04, I dont mind using the terminal, basicly I have a 16gb SSD and the wow folder is like 20gb now so I have to run it on my external HD (NTFS) I know that NTFS has different permissions from EXT3 which is where my problem comes from, I try to run wow.exe in wine (already installed) and i get the error about not marked executable, so I try to mark it and as soon as the check appears it disappears. I read that you can get around this by having it set up to be marked executable before you mount it but my attempts have all failed. Any help would be appreciated! 

(BTW I am running UNR)

---

### Post by eriktheblu on 2011-06-03
Check the permissions on the mount point. NTFS permissions probably don't apply, but the mount point still might.

---

### Post by cawnc4 on 2011-06-03
> **eriktheblu said:**
> Check the permissions on the mount point. NTFS permissions probably don't apply, but the mount point still might.

I have read that before but I dont understand the jargon, If you mean in /Media I have tried but as soon as i make a change it changes back.

---

### Post by frankbooth on 2011-06-03
Maybe adding the drive to fstab with permissions would solve it?

Connect the drive, write:
```

ls /dev/disk/by-uuid -alh

```

Copy the UUID that belongs to the drive and save it for later.

Now write:
```

sudo nano /etc/fstab/

```

Now add the drive by UUID:
```

UUID=INSERT-THE-UUID-HERE /media/INSERTLABELHERE ntfs user,umask=0 0 0

```

I'm not sure if this would give you permission to execute all files, but give it a try.

---

### Post by cawnc4 on 2011-06-03
:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 100 2011-06-03 10:27 .
drwxr-xr-x 6 root root 120 2011-06-03 10:27 ..
lrwxrwxrwx 1 root root  10 2011-06-03 10:02 4032a778-024c-4720-b06f-76d9f10c103f -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-06-03 10:27 66DEEF0EDEEED4F9 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2011-06-03 10:02 ae024f77-6b2f-4de4-b059-5b74f826d550 -> ../../sda5


thats the output and I dont know how to tell which one is which

---

### Post by frankbooth on 2011-06-03
> **cawnc4 said:**
> :~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 100 2011-06-03 10:27 .
drwxr-xr-x 6 root root 120 2011-06-03 10:27 ..
lrwxrwxrwx 1 root root  10 2011-06-03 10:02 4032a778-024c-4720-b06f-76d9f10c103f -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-06-03 10:27 66DEEF0EDEEED4F9 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2011-06-03 10:02 ae024f77-6b2f-4de4-b059-5b74f826d550 -> ../../sda5


thats the output and I dont know how to tell which one is which

lrwxrwxrwx 1 root root  10 2011-06-03 10:27 **66DEEF0EDEEED4F9** -> ../../sdc1

Should be this, but if you want to be sure you could right click the drive and see where it's mounted. (should be /dev/sdc1)

---

### Post by cawnc4 on 2011-06-03
I cant save it, it says error fstab is a directory

EDIT:I took the last / out of the line and got into the real fstab

EDIT2: Now it wont mount, it says line 12 is bad (I am guessing i formated it wrong) the name of the drive in /media is "FreeAgent Drive" can you give me exactly what I need to put in fstab?

---

### Post by cawnc4 on 2011-06-03
bump

---

### Post by frankbooth on 2011-06-03
fstab can't handle spaces, so lets make a new folder...

```

sudo mkdir /media/external

```

and your fstab should look like this:

```

UUID=66DEEF0EDEEED4F9 /media/external ntfs auto,user,umask=0 0 0

```

As you can see in the line above, I added 'auto'. This should make the drive auto-mount on boot if it's connected.

---

### Post by cawnc4 on 2011-06-03
getting the error again, something is still wrong

---

### Post by frankbooth on 2011-06-03
```

UUID=66DEEF0EDEEED4F9 /media/external ntfs nofail,user,umask=0 0 0

```

What about now?

---

### Post by cawnc4 on 2011-06-03
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

---

### Post by frankbooth on 2011-06-03
Hopefully someone else can jump in and help you out, if this doesn't work:
```

UUID=66DEEF0EDEEED4F9 /media/external ntfs nofail,nouser,umask=0 0 0

```

---

