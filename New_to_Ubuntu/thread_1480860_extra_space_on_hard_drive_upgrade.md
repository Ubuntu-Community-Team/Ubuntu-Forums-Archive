---
title: "extra space on hard drive upgrade"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by eddski on 2010-05-12
I bought a hd double the size on my current hd. Now when I go to install the image of the old hd (dual boot with ubuntu and xp) onto the new one, would it be possible to move some of the extra space on the end of the new hd to the first partition?

---

### Post by Ozymandias_117 on 2010-05-12
After you put the image on the new hard drive, you should be able to use gparted to add the extra space to a partition of your choosing. Then when you boot, it will run fsck if it's you're Linux partition, or chkdsk if it's your Windows partition, and the OS should see the new size. 

(Since you have the old hard drive... leave the image on it just in case anything goes wrong)

---

### Post by eddski on 2010-05-13
thanks for the reply, but i was reading about gparted and it seems to have some issues. I just concerned because i have 4 patitions 4 pri., and 1 extended. Win xp is first second is an ntfs partition for data then there is an ext3 part. for /boot then the extended part. w/6 logical partitions in it. I wanted to move the extended to the end.

---

