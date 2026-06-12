---
title: "defrag"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-06-22
how to do a disk defrag from terminal..??  9.10

---

### Post by howefield on 2010-06-22
You don't need to defragment a linux file system, the level of defragmentation you will see is fairly negligible.

---

### Post by bodhi.zazen on 2010-06-22
defrag what exactly ? What makes you think you need to defragment something ?

In general Linux file systems do not fragment anywhere as much as FAT or ntfs and although you may see 1-5 % fragmentation it is insufficient to cause problems.

In general you need at least 25% fragmentation to affect performance and as a comparison I have seen ntfs partitions with 100 % + fragmentation.

The only exception I know to this general rule is if you disk if full to capacity. In that case you would copy (move) the data to another location (off the hard drive) , free up space, and copy the data back.

See: 

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

    [http://www.linuxquestions.org/questions/showthread.php?t=55710](http://www.linuxquestions.org/questions/showthread.php?t=55710)

---

### Post by linux18 on 2010-07-08
if you really want to defrag: 

find ~ -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t

explaination of this command is reply #6 here:

[http://ubuntuforums.org/showthread.php?t=1521138&highlight=defragmentation](http://ubuntuforums.org/showthread.php?t=1521138&highlight=defragmentation)

---

