---
title: "Kubuntu to Kubuntu NFS - folder &quot;does not exist&quot;"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2008-01-16
I've followed the "easy peasy NFS" tutorial here:
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

But I keep just getting:
*"special device 192.168.2.3:media/audio does not exist"*

The server has an IP of 192.168.2.3 and a drive at sdb1 which mounts at /media/audio
The client has an IP of 192.168.2.2 and a folder in /media/superpower/audio created.
Pinging either works fine from either computer.
The user ID number is the same on both computers (1000)


_Here's what I did:_

1. sudo apt-get install nfs-kernel-server nfs-common portmap
2. sudo dpkg-reconfigure portmap (Choose "no")
3. sudo /etc/init.d/portmap restart

4. Adding /media/audio *(rw,no_root_squash,async,subtree_check) to /etc/exports (I also tried 192.168.2.1/24 instead of * as my router is at 192.168.2.1)

5. sudo /etc/init.d/nfs-kernel-server restart
6. sudo exportfs -a

and then on the second computer:

7. sudo mkdir /media/superpower && mkdir /media/superpower/audio
8. chown and chmod both of the folders above
9. sudo mount -t ext3 192.168.3:/media/audio /media/superpower/audio


Any ideas would be very much appreciated. We've been trying to get NFS going for quite a while now without luck! :( Thanks everyone!

---

### Post by chewearn on 2008-01-16
> **Ubuntiac said:**
> 
9. sudo mount -t ext3 192.168.3:/media/audio /media/superpower/audio


1. Is that a typo on the IP address: 192.168.3 (?)
2. Remove "-t ext3":
sudo mount 192.168.2.3:/media/audio /media/superpower/audio

---

### Post by Ubuntiac on 2008-01-16
Thanks Asta!

Yes that was just a typo on the address. Took the -t ext3 out (which I added because I was having another problem) and everything seems to be working great. Thanks for your help!

---

### Post by Ubuntiac on 2008-01-16
Ugh.

OK, it's "working" however the transfer rate is really wierd. It transfers around 200k instantly, then stalls for about a minute and repeats the cycle giving me a speed slower than a 9.6k modem on dialup.

Any ideas?

---

### Post by Ubuntiac on 2008-01-16
Actually, this sounds like a new issue, so I'll post a new thread. I know there's a million other "slow nfs" threads out there, but even they seem to be getting speeds upwards of 5mbs which right now sounds ike a dream to me!

---

