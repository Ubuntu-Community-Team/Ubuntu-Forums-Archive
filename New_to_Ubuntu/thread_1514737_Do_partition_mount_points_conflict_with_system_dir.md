---
title: "Do partition mount points conflict with system directories?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by KonfuseKitty on 2010-06-21
I have read the documentation on partitioning of drives under Ubuntu, and still don't understand this mount point business. Say I create three partitions, one where the system will be installed and mounting as '/' or root, another for documents and testing, mounting as '/var' and a third as swap. Isn't '/var' part of the system directory structure? Would Ubuntu then use the partition as the location for its 'var' folder?

I'm asking this because I've actually created five partitions during the Ubuntu install, mapping them to '/var', '/usr', etc. When I look at the contents, even though I haven't written to them anything myself, they are full of folders and each volume has different folders.

Coming to Linux from the Mac world, I must say the partitioning in Linux is by comparison scary and a kludge. I hope someone can show me how to love it! :p

---

### Post by mbzn on 2010-06-21
Hi,

/var and /usr are both system directories(all the ones on the drop down list at install is).
mounting of other partitions is usually done in /mnt/mountpoint or /media/mountpoint,
At install you'll get best results just using 3 partitions(/[+-8GB]; swap[
+-double your ram] and /home[the rest]). Usually it's easier just putting everything in the /home/username directory and to mount other file systems do it in /media.

For more info read [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/), it should give you a more than good understanding.

---

### Post by Paqman on 2010-06-21
> **KonfuseKitty said:**
> Isn't '/var' part of the system directory structure?

Yep.

> 
 Would Ubuntu then use the partition as the location for its 'var' folder?


Correct.

A mount point is the place in the filesystem that you're attaching some storage to. That storage could be a partition or a whole drive. For example, if you insert a USB stick, the system will automatically mount that stick to a temporary location in /media. Likewise you could mount some network storage to a folder in somewhere like /mnt or /media, or somewhere in your /home.

Where this starts to get useful is things like mounting your whole /home on a separate partition to /. This means you can reinstall the system on /, but leave your home partition untouched. The result is that you can reinstall while retaining all user data and settings.

---

### Post by KonfuseKitty on 2010-06-21
Thank you both, that's great info and much appreciated.

---

