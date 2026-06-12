---
title: "How do I remove ubuntu (dual boot xp and ubuntu)"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Rigorous on 2009-08-10
I want it just to be all xp again, I have both the windows cd and ubuntu cd. I'm all backed-up too. How do I remove ubuntu and give xp back all the space, also, when looking through the partitions I saw smaller other partitions like 20mb,etc. not too big. Are those part of ubuntu?

Thanks

---

### Post by Buuntu on 2009-08-10
You can use the partition editor in the Live CD.  It is under System> Administration > Partition editor.  The other small partition might be a swap, but it should say what it is in partition editor.  From there you can delete the Ubuntu partition (the one that is ext3 filesystem) and increase your XP partition size (NTFS). 

Hope you give Ubuntu a try again in the future.

---

### Post by Rigorous on 2009-08-10
Thanks

---

### Post by joriad on 2009-08-10
Sorry to see you leave us. Might I ask the reason for eliminating Linux from your machine?

---

### Post by hockeyfighter09 on 2009-08-11
You might also need to use the windows cd to get the Windows mbr back so you don't have grub anymore.  Just pop in the Windows cd and choose to repair and type "fixboot" to get windows to boot again without having grub.

---

### Post by misswham on 2009-08-11
If you have the full version of xp just boot from it and download the whole os again.  this should get rid of both old operating systems and start a new.

---

### Post by roharme on 2009-08-11
Insert Windows CD and reinstall Windows.So that Win Loader comes over GRUB Loader.
 
And format the Linux partition

---

### Post by hibliss on 2009-08-11
> **roharme said:**
> Insert Windows CD and reinstall Windows.So that Win Loader comes over GRUB Loader.
 
And format the Linux partition

Why would you do that to a working Windows partition?

---

### Post by Wyphy on 2009-08-11
> **Rigorous said:**
> when looking through the partitions I saw smaller other partitions like 20mb,etc. not too big. Are those part of ubuntu?
If you're using a laptop, those small partitions could be part of a computer restore system. Many laptops have special software that will restore a system to a state like it was when it was brand new.

---

### Post by oedha on 2009-08-11
- use partition editor to erase the ubuntu partition
- boot from windows xp installation cd to it's console
- run fixboot and fixmbr
- reboot ( you will have xp only )

the small partition could be a restore partition or can be left behind partition ( windows left about 8MB )

---

