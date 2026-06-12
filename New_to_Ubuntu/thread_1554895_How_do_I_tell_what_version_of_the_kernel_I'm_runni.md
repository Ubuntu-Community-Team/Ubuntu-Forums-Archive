---
title: "How do I tell what version of the kernel I'm running?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by bamim2 on 2010-08-17
How do I tell what version of the kernel I'm running?

---

### Post by jaycee23 on 2010-08-17
```
uname -r
```

---

### Post by TheStroj on 2010-08-17
Open terminal and type 'uname -a' to get full info, or 'uname -r' for only kernel version.

---

### Post by drs305 on 2010-08-17
Or for GUI, System > Administration > System Monitor (System tab).

---

### Post by bamim2 on 2010-08-17
Thank you all. That was most helpful.

---

### Post by drs305 on 2010-08-17
> **bamim2 said:**
> Thank you all. That was most helpful. 

I updated my kernel & my system wouldn't boot up, so I had to remove the kernel from the Package Manager. Now Grub shows a version of the kernel that I don't have. How do I remove that version of the kernel from showing up in Grub when my system boots up?

Does running "sudo update-grub" do it?

If not, go into synaptic, do a search for the kernel that is showing up which you want removed (such as 2.6.32-22) and remove the associated files (linux-headers-2.6.32-22, etc) then rerun update-grub.

---

