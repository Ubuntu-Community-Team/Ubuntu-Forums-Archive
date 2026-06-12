---
title: "Add more space from windows"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by chamajid on 2011-01-19
Hi,

I installed ubuntu and being a complete novice, I did not set the space properly. The HD is 500GB. Out of that 5gb is going to ubuntu and remaining to windows. So how can I take some space (150 Gb) from windows to use in Ubuntu? Now I am livecd ubuntu with Gparted on. What should I do next?

---

### Post by oldfred on 2011-01-19
Are the partitions next to each other? Is the Ubuntu partition inside the extended  partition? To see your existing partitions:

sudo fdisk -lu

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

