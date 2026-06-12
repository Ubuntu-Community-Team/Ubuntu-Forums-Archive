---
title: "How do I re-install hardy heron over jaunty jackalope?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by writeman on 2009-05-11
Dear Experienced Linux Users:

I should not have tried to fix something that wasn't broken - I had the Oxford English Dictionary working under Wine, my wireless was working and my indexing for searches work. After Jaunty Jackalope install, none of these work. 

Can I insert my hardy heron disk and will the defaults install Heron over Jackalope? I am using Windows from my dual boot to make this inquiry, but would like to get back to a working linux.

Thank you.

Writeman

---

### Post by Paqman on 2009-05-11
I'm not sure if the defaults would overwrite anything. You could well end up with two copies of Ubuntu alongside your Windows. The way to make sure that doesn't happen is to choose "manual partitioning". Make sure you pick the existing ext3 partition, format it and give it the mount point /. Pick your existing swap partition out too.

---

### Post by AndThenWhat on 2009-05-11
Yes your Hardy Heron CD can install over Jaunty.  The default option of the CD will probably wipe the entire disk.  SO, you need to go into the Partition Editor on your Hardy CD (System -> Administration -> Partition Editor) and delete every partition that is not an NTFS filesystem. 

Then when you are ready to install:

Do the partition manually and select the option to install in the largest unallocated space.

---

