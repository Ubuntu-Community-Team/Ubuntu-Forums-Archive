---
title: "Partitioning Scheme Changes"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by carbonbased on 2010-01-26
I've gone from a dual boot system to only Linux, and need to re-arrange my drive partitions to accommodate that change. My drives are:

sda:  150Gb: boot, swap, root partitions for 2 Linux distros (Ubuntu & Linux Mint)
sdb:  1Tb: 500Gb is /home for Ubuntu; 500Gb unused
sdc:  750Gb unused

Being a newbie, what I need to know is how to incorporate the unused space. For example, how would I tell Ubuntu that sdc is to be used for storage? Could I tell Ubuntu to make sdc a part of /home, or just make the mountpoint /anyname?

Can I tell Ubuntu to incorporate the remainder of sdb into /home?

Looks disorganised, and it is, but the migration was from older PC to a hardware retrofit, new hardware, etc. and eventually a test run of Ubuntu. I've made the full switch to Linux and need to clean things up now.

Thanks.

---

### Post by oldfred on 2010-01-26
I have seen several ways. Many just mount /data in /media or /mnt. Some directly mount folders into /home. Others mount it in someother location so it does not show in places and link everything in, my preference.

I have adopted mounting my windows share directly into /home and all my Ubuntu data from another location and replacing all the default folders in /home for data with linked folders from the data partition. 

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

from my history which I have saved to run in other installs.
   21  sudo mkdir /usr/local/fred
   22  sudo mkdir /usr/local/fred/data
edit fstab and reload
   23  sudo mount -a
   64  sudo chown fred:fred /usr/local/fred/data
   72  sudo chown fred:fred /usr/local/fred
   47  sudo chmod 766 /usr/local/fred/data
   24  sudo mkdir /usr/local/fred/data/Documents ( this was a test before I copied all the data from my old install's home)
from home I link everything:
   92  ln -s /usr/local/fred/data/Music
   93  ln -s /usr/local/fred/data/Documents
etc for every folder - my /home now has little or no data, only the hidden config folders and files.

fstab entry:
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2

---

