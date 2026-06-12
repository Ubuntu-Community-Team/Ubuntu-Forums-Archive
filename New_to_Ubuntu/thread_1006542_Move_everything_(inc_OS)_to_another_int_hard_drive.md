---
title: "Move everything (inc OS) to another int hard drive"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by fletcham on 2008-12-09
Hi,

I have two internal hard drives. One is 1TB and just has about 400GB of media on it and the other is 500GB and has ubuntu and evrything else on it, about 200GB available memory. How do i transfer everything over and use the larger drive to boot up from - I will eventually install XP on the smaller one.

Thanks for your help!!!

Fletch :popcorn:

---

### Post by fletcham on 2008-12-09
Hi,

I have two internal hard drives. One is 1TB and just has about 400GB of media on it and the other is 500GB and has ubuntu and everything else on it, about 200GB available memory. How do i transfer everything over and use the larger drive to boot up from - I will eventually install XP on the smaller one.

Thanks for your help!!!

Fletch :popcorn:

---

### Post by Locke_99GS on 2008-12-09
Use gparted to copy and resize the partitions, then fix grub.

---

### Post by rbprogrammer on 2008-12-09
My initial guess would be (and suggest confirmation from another person if not another idea) is to log in recovery mode (command line only) and copy everything over, then remove the smaller hard drive and try to boot that.

The only problem I might foresee is config files within linux that might get a little screwy.

But as stated before, wait for someone else to confirm that this method would work, or wait for another idea.  Obviously there has to be a better idea.

---

### Post by rbprogrammer on 2008-12-09
or you can try to use the LiveCD to copy things over.  That *might* work as well.

---

### Post by Duck2006 on 2008-12-09
Partimage may do what you want to do.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Then you will have to reinstall grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bapoumba on 2008-12-09
Threads merged.

---

### Post by bodhi.zazen on 2008-12-09
Move the partition any way you wish. Then you need to update a few config files.

See this thread : [How to run bleeding edge - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316237")

---

