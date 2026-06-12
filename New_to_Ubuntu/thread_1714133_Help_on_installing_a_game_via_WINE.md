---
title: "Help on installing a game via WINE"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Twinkiers on 2011-03-25
I'm trying to install a certain video game, but I am having trouble doing so.

> For anyone wanting to play Muv-Luv/Alt (or any rUGP games) in wine on  *nix, apply this patch to the wine source code (I used the git version):

Code: [Select]
diff --git a/dlls/msvcrt/mbcs.c b/dlls/msvcrt/mbcs.c
index 5767242..d868a5a 100644
--- a/dlls/msvcrt/mbcs.c
+++ b/dlls/msvcrt/mbcs.c
@@ -1703,13 +1703,13 @@ unsigned char* CDECL _mbspbrk(const unsigned char* str, const unsigned char* acc
 
     while(*str)
     {
-        for(p = accept; *p; p += (MSVCRT_isleadbyte(*p)?2:1) )
+        for(p = accept; *p; p += (_ismbblead(*p)?2:1) )
         {
             if (*p == *str)
-                if( !MSVCRT_isleadbyte(*p) || ( *(p+1) == *(str+1) ) )
+                if( !_ismbblead(*p) || ( *(p+1) == *(str+1) ) )
                      return (unsigned char*)str;
         }
-        str += (MSVCRT_isleadbyte(*str)?2:1);
+        str += (_ismbblead(*str)?2:1);
     }
     return NULL;
 }
-- 
1.7.1
Or  you could grab a native msvcrt.dll from a Windows install and use that  instead. Override the DLL to native in winecfg or set the  WINEDLLOVERRIDE argument in the command line to use the native  msvcrt.dll.

I failed trying to get this patch into wine and I  doubt they'll fix it themselves anytime soon. If someone else wants to  submit this, go ahead. You could probably get it in pretty easily if you  are willing to follow their stupid rules exactly to their liking (be  prepared to defend your full name!).Copypasta from the exact full post.

Now I got an .iso when I downloaded this game...

How do I run it?

---

### Post by Twinkiers on 2011-03-26
Bump

---

### Post by ChrisRatahi on 2011-03-26
.ISO is an image of a disk. You either need to burn it to a cd and use it to install the disk or you can mount it with a suitable application or set of commands.

-- EDIT --

if you cd to the directory with your iso file, use this code to mount to cdrom drive:

```
sudo mount -o loop -t iso9660 (filename).iso /cdrom
```

And when you are done, use this to unmount the iso and free up your cd drive:

```
sudo eject /dev/cdrom
```

That'll make wine see the .ISO as a cd-rom rather than a file. I hope.

---

### Post by Twinkiers on 2011-03-26
> **ChrisRatahi said:**
> .ISO is an image of a disk. You either need to burn it to a cd and use it to install the disk or you can mount it with a suitable application or set of commands.

-- EDIT --

if you cd to the directory with your iso file, use this code to mount to cdrom drive:

```
sudo mount -o loop -t iso9660 (filename).iso /cdrom
```And when you are done, use this to unmount the iso and free up your cd drive:

```
sudo eject /dev/cdrom
```That'll make wine see the .ISO as a cd-rom rather than a file. I hope.
This is what I got:
```
nick@NickDV1000:~$ sudo mount -o loop -t iso9660 MUVLUV_UNLIMITED.ISO/cdrom
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .

```

What do I do next?

---

### Post by ChrisRatahi on 2011-03-26
-- EDIT --

Scrap that, here's a howto... [http://ubuntuforums.org/archive/index.php/t-619250.html]("http://ubuntuforums.org/archive/index.php/t-619250.html")

I hope it helps. :)

---

