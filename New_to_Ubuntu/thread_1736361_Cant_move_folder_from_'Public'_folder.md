---
title: "Cant move folder from 'Public' folder"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by David_UK on 2011-04-22
I've just ripped a CD using Rhythmbox on my desktop PC.  Then I pushed the music files to my netbook over the network.  It's currently sitting in my netbook's 'public' folder, but I fail with an error if I try to paste it anywhere else:
```
There was an error copying the file into /media/Acer/Documents and Settings/User/My Documents/My Music.
Show more details
Not found
```
I think in the past I have rectified problems moving folders imported to public by:
```
sudo chmod -R david:david Foldername
```
But not this time.  I've opened up all the permissions:
```
ls -l
   4 drwxrwxrwx 3 david  david   4096 2011-04-22 14:15 Radiohead
```
Right-clicking on the folder and checking permissions gives:
```
The permissions of 'Radiohead' could not be determined.

```
I'm a bit of a noob when it comes to command line and folder manipulation, so I'd appreciate help.  Thanks

---

### Post by sanguinoso on 2011-04-22
How are you trying to paste into that folder? Drag and drop? Can you post the output of the mount command? ```
mount
```

---

### Post by David_UK on 2011-04-22
> **sanguinoso said:**
> How are you trying to paste into that folder? Drag and drop? 
Right-click>copy, then paste.  All from the GUI.

> **sanguinoso said:**
> Can you post the output of the mount command?

```
david@david-netbook:~/PublicNB$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /media/Acer type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
```
The partition is mounted, in case you were wondering.  I get the same error no matter where I try to paste - Documents, Desktop, Home etc...

---

### Post by JKyleOKC on 2011-04-22
Take a look at the permissions of /media/Acer/Documents since that's where you're attempting to move things TO. The permissions for the item you're trying to move don't count in this case.

However, don't try to change permissions of anything in the /media area or you may make things fail in even worse ways. This directory is managed automatically by the system, when you plug in a USB stick or an external drive, and is NOT intended for general document storage. There should be a folder in your home directory (the one shown initially when you click Places) named Music, that's intended for storing your personal music files. That's the correct place to move it to, and should have no problem.

In general, all of the directories/folders that are outside of your home directory are "off limits" for writing although you can read many of them. This is an integral part of the security model that makes Linux so much more malware-resistant than other systems -- so don't try to change it!

---

### Post by David_UK on 2011-04-22
> **JKyleOKC said:**
> Take a look at the permissions of /media/Acer/Documents since that's where you're attempting to move things TO.
I can paste other files into this folder no problem.  It's full of all my other music files.

> **JKyleOKC said:**
> There should be a folder in your home directory (the one shown initially when you click Places) named Music, that's intended for storing your personal music files. That's the correct place to move it to, and should have no problem.
Pasting to my Ubuntu 'my music' folder fails with the same error.

---

### Post by grvsaxena419 on 2011-04-22
> **David_UK said:**
> 

Pasting to my Ubuntu 'my music' folder fails with the same error.


Try doing 
```
sudo nautilus
```

Browse to the above directory and then try copy and paste .

---

### Post by David_UK on 2011-04-22
Cheers grvsaxena419
Moving the folder as root worked a treat.  Once moved I could then import it into rhythmbox.  I can now also check permissions by right-clicking.
I'm grateful for your help.  I don't really understand why this seemed to 'unstick' the folder (because we didn't actually change anything did we?).

---

### Post by sanguinoso on 2011-04-22
The fact that it succeeded as root implies that there was a permissions error somewhere.

---

### Post by grvsaxena419 on 2011-04-22
> **David_UK said:**
> Cheers grvsaxena419
Moving the folder as root worked a treat.  Once moved I could then import it into rhythmbox.  I can now also check permissions by right-clicking.
I'm grateful for your help.  I don't really understand why this seemed to 'unstick' the folder (because we didn't actually change anything did we?).

Thanks :)
I personally use nautilus as root rather than using commands as root at terminal. :popcorn:
May be some permission changes were left somewhere.

---

