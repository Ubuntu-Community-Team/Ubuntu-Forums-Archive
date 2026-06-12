---
title: "Choosing ext4 over ext3"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Anonono on 2009-05-04
Are there any advantages or disadvantages to using ext4 instead of ext3? I'm doing a reinstall of Ubuntu soon, and would like to know  what one would be the best for me. For 8.04/8.10, I used ext3 fine, so is there any reason to use ext4 over it, or to stay with ext3?

---

### Post by jespdj on 2009-05-04
ext4 is faster compared to ext3. You can find a lot of information about it on the web, try Googling for "linux ext4 filesystem", for example.

[ext4 File System: Introduction and Benchmarks](http://www.linux-mag.com/id/7271)
[A better ext4 filesystem for Linux](http://www.linuxworld.com/news/2008/012908-kernel.html)
[First benchmarks of the ext4 file system](http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html)

---

### Post by Anonono on 2009-05-04
> **jespdj said:**
> ext4 is faster compared to ext3. You can find a lot of information about it on the web, try Googling for "linux ext4 filesystem", for example.

[ext4 File System: Introduction and Benchmarks](http://www.linux-mag.com/id/7271)
[A better ext4 filesystem for Linux](http://www.linuxworld.com/news/2008/012908-kernel.html)
[First benchmarks of the ext4 file system](http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html)
But is it as stable as ext3?

And another thing I forgot to mention, is it okay to do a hard shutdown in ext4? This is probably a dumb question, but it annoyed me in ext3 when Ubuntu crashed and wouldn't get out of it with any of the kill keys, I had to do a hard shutdown, and then it has to do the HDD check the next startup.

---

### Post by kerry_s on 2009-05-04
it's still buggy, some have experienced data loss, my friend said it screwed up 3 installs for him.
so you might want to google first, see what your in for. when i last looked the fix is not due till kernel 2.6.30.

---

### Post by lovinglinux on 2009-05-04
Sticky from the [Installation & Upgrade](http://ubuntuforums.org/forumdisplay.php?f=333) forum

[Ext3 and Ext4: Which file system to install?](http://ubuntuforums.org/showthread.php?t=1133719)

---

### Post by nandemonai on 2009-05-04
Personally I'm sticking with ext3. I don't think the speed benefits outweigh the data loss risk at the moment. Yes you should be doing backups regardless but I'd rather not have to do a restore if I could have avoided it in the first place.

My 2c.

---

### Post by Ivan Kuznetsov on 2009-05-04
Indeed, there's a risk of data loss - see [here]("http://en.wikipedia.org/wiki/Ext4#Delayed_allocation_and_potential_data_loss"), but it has the benefit of [improved booting time]("http://news.softpedia.com/news/Ubuntu-9-04-Boots-in-21-4-Seconds-101885.shtml") and work is ongoing to [address data loss issues]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781").

[I didn't dare to switch]("http://www.ivankuznetsov.com/2009/04/whats-new-in-ubuntu-904-jaunty-jakalope.html") to ext4 in my recent upgrade to 9.04.

---

### Post by The Cog on 2009-05-04
There is an ongoing problem with system lockups and ext4. 
[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824)
My second freeze did enough filesystem damage that I had to reinstall, so I went back to my previous filesystem instead. You don't have to reinstall very often to lose all the extra time you saved in faster boot-ups again.

---

