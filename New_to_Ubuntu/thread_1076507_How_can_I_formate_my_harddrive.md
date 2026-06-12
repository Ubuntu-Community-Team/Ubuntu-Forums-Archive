---
title: "How can I formate my harddrive?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Retro19 on 2009-02-21
I'm trying to formate my harddrive in order to reinstall windows but I can't find any tool for this I've already tried the help&support but without progress.

Help is appreciated.

---

### Post by whoop on 2009-02-21
ubuntu livecd-->terminal-->gksudo gparted

---

### Post by kestrel1 on 2009-02-21
Do you want to keep Ubuntu or not?
If you want to re-install Windows, use the Ubuntu Live CD & then use gparted to delete the partitions that you no longer want, then use the Windows CD & let it format the drive.

---

### Post by Retro19 on 2009-02-21
> **kestrel1 said:**
> Do you want to keep Ubuntu or not?
If you want to re-install Windows, use the Ubuntu Live CD & then use gparted to delete the partitions that you no longer want, then use the Windows CD & let it format the drive.

I want to remove ubuntu. But problem is I try using the menu to start to start it from disc but it ain't rebooting the computer and I tried using the ubuntu live cd and reboot it but it just go into normal.

---

### Post by kestrel1 on 2009-02-21
You need to delete all of your Linux partitions then.
First run the Ubuntu Live CD & go to System -> Administration -> Partition Editor & delete your Linux Partitions. Once you have applied this & the hard drive just has unpartitioned space, reboot your machine with your Windows Cd to re-install Windows.
Can I ask, Why do you want to get rid of Ubuntu? Are you going to use it again?

---

