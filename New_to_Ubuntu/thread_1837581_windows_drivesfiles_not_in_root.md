---
title: "windows drives/files not in root?"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by nimchip on 2011-09-02
I've tried accessing the files of my windows partition on root using
```
gksu nautilus
```but when i open the root folder there are no files, only a desktop icon/folder which shows nothing. I'm using windows 7 and Narwhal. What can I do to see the files?

---

### Post by papibe on 2011-09-02
You don't need to be root. Open Nautilus, the Go -> Computer. There should be a list of partitions. One of them should be your windows partition.

(not sure if this works on a Wubi install).

Regards.

---

### Post by yetiman64 on 2011-09-02
Further to papibe's post, IF it is a wubi install,

> How do I access the Windows drives?

The  Windows partition where you installed Wubi is available as /host within  Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media From [[COLOR=Blue]--Here--[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F")

---

### Post by nimchip on 2011-09-02
Sorry what I meant by "root folder" was actually "host folder". But the rest still applies. There are no files there.
 
Or perhaps I did confuse the two and I'm actually trying to open a root folder... I need to recheck when I get home.
 
And as for papibe's reply: I do need to be root otherwise Ubuntu doesn't let me open the folder.

---

### Post by bcbc on 2011-09-02
On wubi, you don't need root privileges to access /host (someone filed a bug for exactly this reason: full access to all files on windows with no need to elevate privileges).

---

### Post by nimchip on 2011-09-02
Ok I'll double check when I get home. I must have confused the 2 folders after all.

---

