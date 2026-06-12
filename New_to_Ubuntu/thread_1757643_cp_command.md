---
title: "cp command"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by CVGH on 2011-05-13
I'm trying to copy a 4.7GB tar.bz file to a 16GB USB flash drive.
While doing it in a GUI or from the CLI, I get a "File too large"
error.

Why is that?

---

### Post by ~Plue on 2011-05-13
Most probably the flash drive is formated as FAT32 which means there is a 4 GB file size limitation.
You could  either split the file into two parts or format the drive as ntfs or another filesystem which has a larger limit.

---

### Post by CVGH on 2011-05-13
Ah! did not realize that. I thought it might be because it mounted as sdc1 and thought it was a CD. I will look into when I get back to work Monday.

---

