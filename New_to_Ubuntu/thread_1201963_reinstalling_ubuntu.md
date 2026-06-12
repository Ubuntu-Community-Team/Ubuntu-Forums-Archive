---
title: "reinstalling ubuntu"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by duncan503 on 2009-07-01
Could it be possible to reinstall ubuntu without erasing my personal folder? The reason being that for about couple of weeks ubuntu  keep freezing on me without any reason. like doing 3 task @ one ei: listening the Internet radio, surfing the net, and maybe watching utube.
:(
thank you:

---

### Post by renkinjutsu on 2009-07-01
you can do as many installations as you want and keep your personal files! .. so long as your /home is mounted on a different partition. If your /home is on the same partition, you can give this a try 
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

remember, always backup your data before doing anything.

when doing the installation, select manual partitioning, and select your /home partition and mount it at /home (make sure you don't choose to format the partition, or you will lose everything)

---

### Post by Michael.Godawski on 2009-07-01
If you have a separate home partition like described here:

[LIST]
[*][http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[/LIST]
it is.

---

### Post by s3a on 2009-07-01
I love home partitions! It allows you to have your system back to perfection with all your data intact after doing a couple of stupidities to ruin your system lol

---

### Post by prvteprts on 2009-07-01
Yes; as with previous posts, this is possible. My Firefox got ruined after the machine hanged during an update. I just popped in the LiveCD and did pretty much the same: selected the mount point, filesystem, etc. The only thing you have to remember is not to check the "format" option. Oh by the way, my /home is on the same partition.

---

