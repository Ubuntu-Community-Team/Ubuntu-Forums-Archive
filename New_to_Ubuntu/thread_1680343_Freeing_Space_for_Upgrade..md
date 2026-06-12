---
title: "Freeing Space for Upgrade."
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Bolt-On on 2011-02-02
Help needed, please! I've not been using Ubuntu long(started with 9.04, now on 10.10), so I consider myself a novice. After usung Upgrade Manager I got this message - " The upgrade needs a total of 19.9MB free space on disk /boot. Please free an additional 16.7MB of disk space space on /boot. Empty your trash and remove temporary packages of former installations using apt-get clean". Currently , on my 640GB disk, I've got 49MB partitioned as /boot, 2.2GB as swap space, 28GB in /, and 470GB as /home.
     I don't really know how to alter these sizes, and I suspect that I will lose something that is in my /home if I reduce that.

    How can I safely go about doing what the message asks? Any advice is needed and will be much appreciated.

---

### Post by TeoBigusGeekus on 2011-02-02
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1678065") thread.

---

### Post by snowpine on 2011-02-02
Wow, 49mb for /boot is tiny, no wonder you are having problems!

I would recommend:

1. BACK UP all data to an external drive
2. Boot with an Ubuntu Live CD
3. Use the GParted Partition Editor to shrink whichever partition is adjacent to /boot and then make /boot bigger.

I would recommend at least 200mb for /boot. It depends how many kernels you like to keep at any given time.

You'll find some good general partitioning info here: [http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by TeoBigusGeekus on 2011-02-02
Nah, 48mb should be enough, as long as he/she cares to delete the old ones after a number of kernel updates.

---

