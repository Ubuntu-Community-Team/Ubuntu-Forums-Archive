---
title: "System Restore subsitute"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-03
Okay I had enough. I done things on Ubuntu which gave me weird problems, which I solve by uninstalling Ubuntu and reinstalling it (I use wubi). But then, I would need to download all the updates again, redo everything, spending at least an hour or two. I don't care about my personal files, but is there any system restore substitute for Ubuntu?

I tried:

Back in time: Couldn't figure how to use it. After specifying it to make a backup of my /home folder, it created a 44kb file. I right-clicked it and chose "restore", to see how it worked, but nothing happened. Uninstalled.

Tar: I used this guide.
```
http://ubuntuforums.org/showthread.php?t=35087
```
But I could not understand the second step where they wrote "and go to the root of your filesystem (we use this in our example, but  you can go anywhere you want your backup to end up, including remote or  removable drives.)" and gave the example of "/cd". Problem is I don't see anything when I type /cd into the terminal.

Remastersys: I used this guide.

```
http://www.psychocats.net/ubuntu/remastersys
```
But I could not understand what was meant by "Then copy the appropriate settings directories to the /etc/skel directory."



So does anyone else have any other way for me to backup my ubuntu? I don't really care about my personal files.

---

### Post by indytim on 2011-02-03
I've been using fsarchiver quite successfully for the past 6 months or so.  It does partition level backups (like Partimage).  See my sig on the Backup Strategy V2 for details.

IndyTim / DataMan

---

### Post by bcbc on 2011-02-03
If you're using Wubi, just copy the entire virtual disk, the root.disk file (c:\ubuntu\disks\root.disk). Copy back over when having problems.

Wubi has problems with grub - so locking the grub-pc and grub-common packages will save you from these issues. See [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.

Also, avoid hard shutdowns of Wubi - if it hangs use ALT+SysRQ R-E-I-S-U-B instead.

Finally, run chkdsk on windows and try defragmenting before installing Wubi to make sure the ntfs filesystem is clean and the root.disk isn't excessively fragmented.

---

### Post by flee0308 on 2011-02-06
> **bcbc said:**
> 

Also, avoid hard shutdowns of Wubi - if it hangs use ALT+SysRQ R-E-I-S-U-B instead.


Thanks for the tip, I made my backup. :D

What is ALT+sysRQ R-E-I-S-U-B though?

---

### Post by bcbc on 2011-02-06
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
```
unRaw      (take control of keyboard back from X),  
 tErminate (send SIGTERM to all processes, allowing them to terminate gracefully),
 kIll      (send SIGKILL to all processes, forcing them to terminate immediately), 
  Sync     (flush data to disk),
  Unmount  (remount all filesystems read-only),
reBoot.
```

---

