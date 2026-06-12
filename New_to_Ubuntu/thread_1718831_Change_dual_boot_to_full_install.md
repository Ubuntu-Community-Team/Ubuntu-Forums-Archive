---
title: "Change dual boot to full install?"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by lumop on 2011-03-31
I have windows vista and I've only used the trial of Ubuntu. I want to dual boot Ubuntu with vista. If I am dual booting them and ever decide I want to wipe out vista and only have Ubuntu on my hard drive, is there a way to do that? Also, if I do, will Ubuntu save all the settings, downloads, and files I would have on it or would it totally reset?

---

### Post by ubudog on 2011-03-31
If you ever want to do that, this is what you should do.  
1. BACKUP YOUR STUFF
2. BACK IT UP!
3. Boot a live cd of Ubuntu.  
4. Open Gparted (System>Administration>Gparted Partition Editor)
5. Select your Windows partition (be sure it's the right one), right click, and select delete.
6. Wait for it to complete, then do the same for the Windows recovery partition.  (once again, make sure it is the right one)

7. Open a terminal.  (Applications>Accessories>Terminal)

```
sudo update-grub
```
(This updates your boot menu entries, to get rid of Windows)

8. Reboot and enjoy a Windows free system.


IF ANYTHING HAPPENS  (and you don't care about Windows anymore)

and everything is wiped out, your computer is messed up, you have backups, then follow the following to get yourself to an Ubuntu only system.

1.  Boot the Ubuntu Live CD and reinstall, using Guided - Full Drive at the partitions menu.

2. Reboot, and copy your stuff back over from your external hard drive, USB drive, whatever.

All righty, hope that helps.  Let me know if you have any questions before attempting, just to make sure we don't mess anything up.  :)

---

### Post by lumop on 2011-04-01
Thanks for the details. If I ever want to I'll refer back to this.

---

### Post by rewyllys on 2011-04-01
> **lumop said:**
> . . . . Also, if I do, will Ubuntu save all the settings, downloads, and files I would have on it or would it totally reset?
When using Linux, the best way to ensure that your settings, downloads, and files will be preserved through system changes is by putting your "/home" directory on a separate partition--separate, that is, from the partition that contains your root, or "/", directory.

---

