---
title: "What is a root path?"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by ichigo6420 on 2011-03-20
What does it do and how do you get there?

---

### Post by kroq-gar78 on 2011-03-20
The "root path" is where everything is stored. Everything (pictures, movies, files, folders, etc.) are all stored *somewhere* in there. Most of your documents, etc. are stored in the folder '/home/'


is the "filesystem root", which is pretty much "root path". If you post the cont4ext in which you found "root path", then maybe I can be more specific, for it can be a little different.

---

### Post by deconstrained on 2011-03-20
/

---

### Post by cgroza on 2011-03-20
```
cd /
ls
```

There it is, in all its might!

---

### Post by ichigo6420 on 2011-03-21
I found it on this link, on the second reply to the question: [http://ubuntuforums.org/showthread.php?t=1492241](http://ubuntuforums.org/showthread.php?t=1492241)

I have the same problem as the asker, but I don't understand the vocabulary. So yeaaah.

---

### Post by Hedgehog1 on 2011-03-21
I think I understand what you are asking (at least I hope so).

Linux and Unix use a 'base' location for the "file system" to begin.

It shows as '/' (said 'root')

From this, all other directories and devices are 'attached' or 'mounted'

So from '/', we have:

/etc
/home
/tmp
/usr

Everything lives in the file system in Linux (and in all Unix's).

Need to reach a CDROM?

You can find it here:

/cdrom

Or here

/media/cdrom

I hope this makes sense.

When we talk about the '/' or root, we need to tell Linux what partition is ***the*** partition where the base directory of '/' is found.

We do that when we install Ubuntu, either automatically for us or we can assign it ourselves:

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]

See how the /dev/sda5 partition is told that it will be the '/' partition?

After installation, you can see this information in the **/etc/fstab** (**F**ile **S**ystem **TAB**le) file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
**[COLOR="red"]# / was on /dev/sda5 during installation[/COLOR]**
UUID=f2fd03c5-2835-415c-8448-75473daf624a  **[COLOR="Red"]/[/COLOR]**                 ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0  
```

Does this make some sense now?  I do hope so.  Not everyone gets these things right away; they can be hard concepts.

***The Hedge***

:KS

p.s. Here is a link to some other examples of /etc/fstab and it use: [How Linux makes larger 'file systems' using /etc/fstab]("http://ubuntuforums.org/showthread.php?t=1705788")

---

### Post by Drenriza on 2011-03-21
Open a terminal and type
```
man hier 7 
```

---

