---
title: "uderstanding storage space in linux...."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-17
OK for my setup i just installed ubuntu on a 20.G hard drive and told it to use the guided full disk....Now coming from windows how can i understand how the space is laid out....basically im going to install VMware or Virtual box and would like to carve out a space to put it...anyone have any good articles or can expalin it to me. or when i do the install how is the best way to lay out the partitions?

below is a df output 

/dev/sdb1             18543888   3625248  13984064  21% /
varrun                  646972       100    646872   1% /var/run
varlock                 646972         0    646972   0% /var/lock
udev                    646972        56    646916   1% /dev
devshm                  646972       156    646816   1% /dev/shm
lrm                     646972     39788    607184   7% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      18543888   3625248  13984064  21% /home/luke/.gvfs

---

### Post by rlunger on 2008-12-17
> **luke0927 said:**
> OK for my setup i just installed ubuntu on a 20.G hard drive and told it to use the guided full disk....No coming from windows how can i understand how the space is laid out....basically im going to install VMware or Virtual box and would like to carve out a space to put it...anyone have any good articles or can expalin it to me. or when i do the install how is the best way to lay out the partitions?

below is a df output 

/dev/sdb1             18543888   3625248  13984064  21% /
varrun                  646972       100    646872   1% /var/run
varlock                 646972         0    646972   0% /var/lock
udev                    646972        56    646916   1% /dev
devshm                  646972       156    646816   1% /dev/shm
lrm                     646972     39788    607184   7% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      18543888   3625248  13984064  21% /home/luke/.gvfs

If you're going to use virtualization software (VMware or VBox), you probably don't need a separate partition.  I don't have experience with VMware, but I use VBox.  VBox sets up a virtual drive, which is just a file in your linux system that looks like a drive to the virtual machine.  Linux or Windows or whatever OS you use inside the VM will partition, format, and write to this file just as though it were a physical drive.

---

### Post by luke0927 on 2008-12-17
Thanks i haven't used VMware yet but i can get it through work and thought about playing around with it....what about if you want to just have a partition carved out to store things.  

How do disk show up in ubuntu or linux sdb1 would be driver and if i had another drive or partion it would be sdb2 right?

---

### Post by rlunger on 2008-12-17
> **luke0927 said:**
> Thanks i haven't used VMware yet but i can get it through work and thought about playing around with it....what about if you want to just have a partition carved out to store things.  

How do disk show up in ubuntu or linux sdb1 would be driver and if i had another drive or partion it would be sdb2 right?

sdb is the physical drive you're using.  sdb1 is the first partition on that drive.  If you were to set up another partition, it would be sdb2, unless it was an extended partition, in which case it would be sdb5 and sdb6 (extended partition containing a second logical partition).  A different drive would have a different letter, such as sdc or sdd, and each of these would have their own partition numbering.  Hope this answers your question

---

### Post by luke0927 on 2008-12-17
> **rlunger said:**
> sdb is the physical drive you're using.  sdb1 is the first partition on that drive.  If you were to set up another partition, it would be sdb2, unless it was an extended partition, in which case it would be sdb5 and sdb6 (extended partition containing a second logical partition).  A different drive would have a different letter, such as sdc or sdd, and each of these would have their own partition numbering.  Hope this answers your question

Thanks that does help....

---

### Post by simtaalo on 2008-12-17
if you want a fuller explanation behind storage space and partitioning checkout this article [http://content.hccfl.edu/pollock/AUnix1/Partitioning.htm](http://content.hccfl.edu/pollock/AUnix1/Partitioning.htm)

---

### Post by snova on 2008-12-17
> **luke0927 said:**
> OK for my setup i just installed ubuntu on a 20.G hard drive and told it to use the guided full disk....Now coming from windows how can i understand how the space is laid out....basically im going to install VMware or Virtual box and would like to carve out a space to put it...anyone have any good articles or can expalin it to me. or when i do the install how is the best way to lay out the partitions?

below is a df output 

/dev/sdb1             18543888   3625248  13984064  21% /
varrun                  646972       100    646872   1% /var/run
varlock                 646972         0    646972   0% /var/lock
udev                    646972        56    646916   1% /dev
devshm                  646972       156    646816   1% /dev/shm
lrm                     646972     39788    607184   7% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      18543888   3625248  13984064  21% /home/luke/.gvfs

Most of those aren't actual partitions. Only the first one is, actually, because it begins with "/dev/sd". The rest don't correspond to hardware.

You don't need a new partition for either VMware or VirtualBox. They put the virtual hard disk in a (rather large) file.

---

### Post by luke0927 on 2008-12-17
Thanks for the help...

---

