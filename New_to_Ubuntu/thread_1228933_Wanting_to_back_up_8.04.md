---
title: "Wanting to back up 8.04"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by L Campbell on 2009-08-01
I'm using 8.04 on a PC and intend to update it to 8.04.3

In order to backup my current system, is Pybackpack a favorite tool to use, or is there something that would be better?

TIA

---

### Post by louieb on 2009-08-01
If you have been keeping up with the normal security  updates then you should already be at 8.04.3.

As far a backup goes I prefer partimage. [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") but if feel you need to be able to recover individual files then tar would be a good way to go. [Howto: Backup and restore your system! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup")

---

### Post by L Campbell on 2009-08-01
> **louieb said:**
> If you have been keeping up with the normal security  updates then you should already be at 8.04.3.

As far a backup goes I prefer partimage. [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") but if feel you need to be able to recover individual files then tar would be a good way to go. [Howto: Backup and restore your system! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup")

Thanks, I tried ' Howto: Backup and restore your system! - Ubuntu Forums ' but, after 95 pages and 948 posts (OK, so I didn't read ALL of them) it seems like there is no 'favorite' way to do this.     :-(

---

### Post by louieb on 2009-08-01
lol haven't read them all either. 
But got to looking around and found another pretty good one on tar.
This guy goes into daily backups and explains some more of the restore options. [Howto: Backup your PC using "tar" -  Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1019517&highlight=tar+backup")

---

### Post by Zill on 2009-08-01
L Campbell:  As already pointed out by louieb your OS should automatically update.

If you want to check your current installed version use this code:
```
cat /etc/issue
```

---

### Post by LewRockwell on 2009-08-01
of course, using Clonezilla and becoming comfortable with it means that you can back-up/clone virtually any data in any format from any operating system

[http://www.clonezilla.org/](http://www.clonezilla.org/)

.

---

### Post by L Campbell on 2009-08-01
> **LewRockwell said:**
> of course, using Clonezilla and becoming comfortable with it means that you can back-up/clone virtually any data in any format from any operating system

[http://www.clonezilla.org/](http://www.clonezilla.org/)

.

That looks rather interesting.

THANKS.

---

### Post by PhoHammer on 2009-08-01
There is also remastersys ([http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)) , 
but I would go Zill and check to see if you're not already up to date...

---

### Post by MelDJ on 2009-08-02
there is also Reconstructor

---

### Post by slakkie on 2009-08-02
> **LewRockwell said:**
> of course, using Clonezilla and becoming comfortable with it means that you can back-up/clone virtually any data in any format from any operating system

[http://www.clonezilla.org/](http://www.clonezilla.org/)

.
Thanks, just burned my livecd and made a backup of 8.04 before I upgraded my OS.

Interface could be improved, but other then that, looks great.

---

