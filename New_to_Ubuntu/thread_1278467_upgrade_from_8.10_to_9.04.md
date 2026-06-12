---
title: "upgrade from 8.10 to 9.04"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by mustard greens on 2009-09-29
I am interested in upgrading from 8.10 to 9.04 via the network (update manager), but have no way currently to back up my system.  I do have my home folder on a separate partition.  is there any chance of the upgrade effecting my home partition?

---

### Post by ibizatunes on 2009-09-29
By default you dont have a serparte home folder, generally upgrade is safe (ish), but it better to do a clean install of 9.04,
how much data do you have to back up?

---

### Post by mustard greens on 2009-09-29
I thought about the clean install, but was unsure how it works now that I am on separate partitions.  when the live CD gets to the issue of partitioning how should I proceed?

---

### Post by scc4fun on 2009-09-29
> **mustard greens said:**
> I thought about the clean install, but was unsure how it works now that I am on separate partitions.  when the live CD gets to the issue of partitioning how should I proceed?

I'm not an expert, but you should be able to select the separate partition as your /home and the other main partition as / (root) or everything else.

---

### Post by diesch on 2009-09-29
> **mustard greens said:**
> I am interested in upgrading from 8.10 to 9.04 via the network (update manager), but have no way currently to back up my system.  I do have my home folder on a separate partition.  is there any chance of the upgrade effecting my home partition?

The upgrade itself doesn't touch the home partition. But some of the upgraded programs may upgrade their data in your home when you start them.

---

### Post by mustard greens on 2009-09-29
I already have partitions which I would like to keep as they are.  I believe I only want to install on the root partition but am not sure how to do that.

---

### Post by crewkid89 on 2009-09-29
When you get to the point in the install, select manual and then indicate which partitions you want mounted for each (root partition for /root, home partition for /home etc.)  If you want to keep your current home partition just make sure you do NOT select format on it.

---

### Post by mustard greens on 2009-10-02
so I borrowed a flash drive to back up my critical documents and decided to run the network update.  it worked flawlessly.  thanks to all who gave their advice.

---

### Post by nhasian on 2009-10-02
good thing you finally upgraded to 9.04.  At the end of this month when 9.10 is released, you can easily upgrade to that as well using the same method.  :)

---

