---
title: "how to uninstall ubuntu 'side by side' by windows"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by blizta on 2010-03-02
hi everyone.....:)

i just want to know how do i uninstall ubuntu that installed side by side by windows xp?? :D

---

### Post by Ozymandias_117 on 2010-03-02
Screw it, they answered ya =P Apparently I can't be helpful at midnight >.<

---

### Post by bcbc on 2010-03-02
You can delete the ubuntu partition - but you first have to restore the MBR so that it boots windows. Right now you probably have grub in the MBR and when ubuntu is gone, that won't do squat.
So either use your xp recovery to restore the mbr or you can put lilo on it, and then kill the ubuntu partition and recreate under windows and format as ntfs.

Restore MBR:
1. Boot using XP recovery CD
2. Run:
```
fixmbr
```
3. remove CD, type exit and enter to reboot pc

(From then on you won't be able to boot ubuntu - you might want to backup any ubuntu data files first)
Good luck. If you need help with the above post back.

PS if you actually installed wubi (it doesn't sound like you did, but just in case), then go to Control panel, Add/Remove programs and uninstall from there.

---

### Post by Gone fishing on 2010-03-02
What a strange thing to want to do - However:

You need to delete the Ubuntu partitions - this can be done in windows. Control Panel > Administrative Tools > Computer management and under disk management you can delete the partitions created by Ubuntu. Be careful you can do damage here they will appear in XP as unknown partitions. You can then replace them with a NTFS partition that will appear as a new drive with  letter.

Next boot up on you XP CD press R when asked to repair windows and run the command FIXMBR.

Done.

---

### Post by blizta on 2010-04-12
thanks everybody......................:guitar:

---

