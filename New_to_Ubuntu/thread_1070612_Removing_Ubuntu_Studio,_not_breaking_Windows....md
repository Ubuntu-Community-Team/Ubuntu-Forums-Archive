---
title: "Removing Ubuntu Studio, not breaking Windows..."
date: 2009-02-15
forum: New to Ubuntu
---

### Post by sambront on 2009-02-15
I'm dual booting one of my desktops with Vista and Ubuntu Studio. 

Ubuntu is on a partition on a second drive, and I need to free up the space. Can I just kill the partition and reclaim the space, or will that screw up GRUB?

I don't care if GRUB still shows up and offers Ubuntu as an option that does nothing, but I don't want to screw up Windows (this is my gaming machine, and I don't want to have to spend days re-installing, etc).

Thanks in advance.

---

### Post by zvacet on 2009-02-15
Check [this.]("http://ubuntuforums.org/showthread.php?t=508927&highlight=uninstall+ubuntu")

---

### Post by ithanium on 2009-02-15
I guess deleting the partition with Ubuntu will do the job, but wait for other advices before you do so :D

---

### Post by kk0sse54 on 2009-02-15
> **ithanium said:**
> I guess deleting the partition with Ubuntu will do the job, but wait for other advices before you do so :D

You can delete the Ubuntu partition through gparted and a Ubuntu liveCD however grub was installed on the /boot folder on the Ubuntu partition so you won't be able to boot into windows until you restore your mbr hence the link given by zvacet.

---

