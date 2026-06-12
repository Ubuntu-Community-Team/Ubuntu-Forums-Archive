---
title: "Cannot Unmount ext3 to partition with Gparted 9.04"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by kristine12 on 2009-11-20
I want to create partition on my 500 GB HDD to install my Windows Vista Ultimate. When I install Ubuntu I decided to use the entire disk but now I decided to use them both. I try to shrink the volume by using Gparted but the menus are disabled. It shows the following prompt: 

"The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."

How do I unmount ext3 manually and creating new partition without harming my data?

---

### Post by rideburton56 on 2009-11-20
Are you running GPartEd after starting up Ubuntu?  You need a live CD to partition, because otherwise the HD gets mounted to start up the OS.

---

### Post by Shazaam on 2009-11-20
Hi and welcome.
You cannot safely unmount a partition that is in use. It looks like you are running gparted while at your desktop. The best way IMHO to run gparted is either by booting the Ubuntu livecd (instead of your running system) or by booting the standalone version of gparted...
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by kristine12 on 2009-11-20
Not yet, but I will try it.

---

### Post by kristine12 on 2009-11-20
If I booted Ubuntu 9.04 and modify the partition would this harm my data?

---

### Post by Darce on 2009-11-20
You should ALWAYS backup before making changes to partitions      :)

---

### Post by kristine12 on 2009-11-20
> **Darce said:**
> You should ALWAYS backup before making changes to partitions      :)


:(
How would I backup my data?
](*,)

And if all things doesn't work right. Do I need to install again Ubuntu and all installed components?
What is the safest way in creating new partition without losing the data?

---

### Post by kristine12 on 2009-11-20
I have successfully shrink the partition using the Ubuntu Live CD and my files & data are unaffected. Thanks a lot guys! This saves me a lot of time! :KS

---

