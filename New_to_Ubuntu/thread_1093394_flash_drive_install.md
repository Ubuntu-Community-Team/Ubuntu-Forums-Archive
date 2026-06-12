---
title: "flash drive install"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by tim1970 on 2009-03-11
I was able to create a boot USB disk, so now I have a persistent copy of 8.10 to run on any machine.  However when I try to run updates, it fails about half way through.  I have a 16GB flash drive, but I only allocated 4GB for Ubuntu.  Could this be my problem?  What is the recommended allocation to be able to run off of a flash drive.

Thanks

Tim

---

### Post by kanikilu on 2009-03-11
> **tim1970 said:**
> However when I try to run updates, it fails about half way through. How does it fail? Does it give any errors? Anything useful in the logs?

> I have a 16GB flash drive, but I only allocated 4GB for Ubuntu.  Could this be my problem?  What is the recommended allocation to be able to run off of a flash drive. I know I run pretty close to the limit on my EeePC's solid state drive (4GB model), so that could be your issue. Try running ```
df -h /
``` to see your disk usage.

You can also try running ```
sudo apt-get clean
``` to quickly and easily reclaim some disk space.

---

### Post by tim1970 on 2009-03-11
> **kanikilu said:**
> How does it fail? Does it give any errors? Anything useful in the logs?



 I know I run pretty close to the limit on my EeePC's solid state drive (4GB model), so that could be your issue. Try running ```
df -h /
``` to see your disk usage.



You can also try running ```
sudo apt-get clean
``` to quickly and easily reclaim some disk space.


How do I check the Logs?


Here is my disk Usage:

Disk usage:
Size = 4.0 G
used = 2.2G
Avail = 1.6G
use% = 59%

I apologize for not having the exact error message (I should know better. :(   I will try to update again tonight when I get home)

Also, is it even possible to have a persistent area > 4GB since this is on a FAT32 flash drive?


thanks again

Tim

---

### Post by kanikilu on 2009-03-11
> **tim1970 said:**
> How do I check the Logs? The /var/logs/ directory is usually the place to look. I think apt has it's own log, but it wouldn't hurt to check the system log, messages, etc.

> Here is my disk Usage:

Disk usage:
Size = 4.0 G
used = 2.2G
Avail = 1.6G
use% = 59% So you have plenty of free space for now. That's probably not why the update is failing then. See if you can get the exact error message later.

> Also, is it even possible to have a persistent area > 4GB since this is on a FAT32 flash drive? I'm not sure, does it partition the flash drive, or is there some single "file" it all goes into? I don't really know...

I'm guessing it's a partition, in which case it doesn't matter if it's over 4GB. To check, plug the flash drive into another Ubuntu computer, if you have one available, and the output of ```
sudo fdisk -l
``` should tell you if it's a 4GB partition. If that's the case, you can probably use gparted to increase the size if you want to.

---

### Post by tim1970 on 2009-03-11
I was able to find the log file from when I ran my updates.

Here is what it the tail end of it says......


Setting up libapparmor-perl (2.3+1289-0ubuntu4.1) ...
Setting up apparmor-utils (2.3+1289-0ubuntu4.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
  linux-image-2.6.27-7-generic
Log ended: 2009-03-10 05:47:24

And if I remember right, there was not a more descriptive error message when I was running updates.

Tim

---

### Post by kanikilu on 2009-03-11
Hmm, can you try clearing the update cache (sudo apt-get clean) and trying again (sudo apt-get update && sudo apt-get upgrade)?

Also, I'm not sure, but the syslog may give you a little more detail on the error.

---

