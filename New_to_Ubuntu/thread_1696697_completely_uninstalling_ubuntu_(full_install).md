---
title: "completely uninstalling ubuntu (full install)"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by frenkyou on 2011-02-27
my computer wouldn't dual boot windows and ubuntu so i did a full install with ubuntu 10.04. i was wondering if there was any way to delete ubuntu and go back to windows? my dell inspiron 15r didn't come with a windows cd, just had windows on it. i've been looking all over and can't find anything about this.

---

### Post by Hedgehog1 on 2011-02-27
> **frenkyou said:**
> my computer wouldn't dual boot windows and ubuntu so i did a full install with ubuntu 10.04. i was wondering if there was any way to delete ubuntu and go back to windows? my dell inspiron 15r didn't come with a windows cd, just had windows on it. i've been looking all over and can't find anything about this.

Sorry find yourself in this situation. Before you overwrote the disk drive it was possible to backup windows so you could restore it, but that option is gone.

If you re-install windows, you will have to obtain a copy; most like by an upgrade version (assuming you have the windows license sticker on your PC with the serial number for the OS).

Can you scrape by on your Ubuntu install until you can locate (or buy) windows disks?:confused:

:KS

---

### Post by fbicknel on 2011-02-27
Why not try installing 10.10?  Maybe it will have better support for your h/w.  

Once you get it running, you can install VirtualBox (Oracle) and put your Winders on that.  

I have all my home computers and my work laptop running Ubuntu, and four of those run VirtualBox to get at that one or two cranky Windows apps I can't do without.

If nothing else, you can practice installing Ubuntu and Windows!  <grin>

---

### Post by jeremyjjbrown on 2011-02-27
> **frenkyou said:**
> my computer wouldn't dual boot windows and ubuntu so i did a full install with ubuntu 10.04. i was wondering if there was any way to delete ubuntu and go back to windows? my dell inspiron 15r didn't come with a windows cd, just had windows on it. i've been looking all over and can't find anything about this.

Did you overwrite the Windows Partition? If it still there you can restore Windows

put this in a terminal and post the results 

```
gedit /etc/fstab
```

If the NTFS partition is still there you can try to rewrite the Windows master boot record. It's the software that launches Windows that GRUB replaces.

You will need some kind of windows startup disk to boot to you can view the commands here.
kb.acronis.com/content/1507

If you only have the Ubuntu Livecd try this out.
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Good Luck!

---

