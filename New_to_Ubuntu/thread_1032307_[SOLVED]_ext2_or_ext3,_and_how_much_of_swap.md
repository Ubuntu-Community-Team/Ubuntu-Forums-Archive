---
title: "[SOLVED] ext2 or ext3, and how much of swap?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-06
Hello, me again!

I was wondering, what size my swap partition should be? And Should I format Linux partition to ext2 or ext3? Whats the best for Ubuntu 8.10, my system is Athlon64 x2, 2GB of RAM...
I Have installed Mandriva 2009 One to ext3 with 1084MB of swap, it worked okay(but uninstalled becouse of those .rpm-s), should I do the same with Ubuntu?

---

### Post by porchrat on 2009-01-06
In order to hibernate properly your system should have at least as much swap as you do RAM.  I would recommend ext3 over ext2 for the journaling capabilities.

---

### Post by opticyclic on 2009-01-06
I believe that ext3 is the 'better' option now since it has journaling
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Some people will recommend the Linux-Swap partition to be 2x your RAM.

Read here for further info about these subjects
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by neurostu on 2009-01-06
If you want to hibernate then you'll need MORE swap then ram.  If you have lots of ram (more then 1gb) then you really only need about 512mb of Swap. If your HDD is big enough then make a swap file as big as your ram, but if you're worried about running out of HDD then make your swap file smaller and just don't hibernate.

You probably won't ever end up using your swap, but if you don't have it turned on you will see a performance hit, especially if you do anything that requires storing and processing a lot of data.

As far as ext3 vs ext2 I would recommend ext3, its the newer of the two.

Also it sounds like you're doing a new install, I would HIGHLY recommend you create a /home partition as well. It will save you a lot of work and pain!

---

### Post by Ben Page on 2009-01-06
Thnx for the nfo, guys!

---

