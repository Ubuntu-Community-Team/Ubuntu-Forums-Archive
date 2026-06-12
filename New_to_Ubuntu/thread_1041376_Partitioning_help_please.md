---
title: "Partitioning help please"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Tony1949 on 2009-01-16
Hi, I tried to install Ubuntu 7.04 onto my computer which has windows XP. At step 4 I chose 'guided' -it loaded but erased XP. I've put XP back on and now would like to try 'manual' but don't understand how. At 'Prepare Partitions' I get:

/dev/sda
/dev/sda1/ntfs/media/sda1    40007MB    3900MB
free space                    8MB

I've no idea what all this means -but I'd like to know.
I would be grateful if someone could tell me what to write -And, more important, why!

I don't understand what 'mount point"/"' means or how to do it.

Thanks.

---

### Post by Ben Page on 2009-01-16
don't know about 7.04, but on 8.10 this means you got two partitions, one 40GB and other 4GB (but im not sure)

the 'mount point"/"' means - the mounting point of your root for Linux (like c:\ for Windows). So, mount as root that partition to witch you would like to install Linux (this has to be done, or Linux wont install). To mount root to partition, select partition you wish to be the root partition for Linux and click "edit", there select "mount point /" for that partition and click OK (confirm your selection), and youre good to go.

---

### Post by mapes12 on 2009-01-16
If you try again then when you get to the same part of the install select "Use fee space"option. I'm working from memory. This should setup a dual boot XP and Ubuntu configuration. If you need some more free space then use GParted (it's free & Google it) to create some more space for Ubuntu. Additionally, click the link in my signature file for full tutorials.

---

### Post by Tony1949 on 2009-01-17
Many thanks gents! All is now OK. It does seem that my Ubuntu behaves differently each time I use the partitioner ~ it's time I got to understand all this. Thanks again.

---

