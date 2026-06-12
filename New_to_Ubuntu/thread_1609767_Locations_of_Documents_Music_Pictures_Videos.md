---
title: "Locations of Documents Music Pictures Videos?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by kendoori on 2010-10-30
Am setting up a new system for a friend who has a 650Gb drive. I installed 10.10, and set up separate partitions for home, swap, everything else, and left 300gb for "data," assuming this would allow easiest backup and management.

Is it a good idea to just point the default file locations (I have Ubuntu tweak installed) to folders that I create off of the root of the "data" partition, or is the exercise of keeping all working documents, images, etc... on a separate partition, and just leave everything in \home?

---

### Post by akand074 on 2010-10-30
Why would you not make /home your data partition :S. Will you be using windows as well?

---

### Post by kendoori on 2010-10-30
> **akand074 said:**
> Why would you not make /home your data partition :S. Will you be using windows as well?

No Windows. My thinking was that having a separate data partition would make backing up settings and programs easier and less unwieldy. For example if one has a lot of music, or video, and everything is kept in the default home, than backing up of config becomes harder.

Do you think most people that create a separate home partition, just leave it that way, even if they have 100s of gb of user files?

---

### Post by akand074 on 2010-10-30
Most people use /home as their data partition. I have an entire hard drive (1TB) dedicated to /home. That is almost full now to tell you the truth. Thats the whole point though /home is your data location in the file system. Putting it as a separate partition is very beneficial because not only to you keep your data when you do clean installs or your system is destroyed, you also have all your configuration files. Theres no point having another data partition its just repetitive.

---

