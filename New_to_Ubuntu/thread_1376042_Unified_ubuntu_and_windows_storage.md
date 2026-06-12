---
title: "Unified ubuntu and windows storage"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Dj Dutchman on 2010-01-08
Hi, I have both windows and Ubuntu installed on my laptop. I use my Ubuntu partition on a day-to-day basis but I DJ off my windows partition (Virtual DJ). All my music was stored in my Ubuntu partition but I needed to access it from my windows partition as well. I therefore created a ntfs partition that acted as a unified storage space for both my Ubuntu and windows partitions. I have two questions, 1) How do I make the storage space automount on login and 2) is it possible that the contents of my home directory point to this storage space, i.e. if I store something in /home/user/Pictures it is actually stored in a folder called Pictures in said storage space, while of course leaving everything else the way it is. There is only one user so it doesn't need to be the contents of /home but the contents of /home/myusername.

Many thanks...

---

### Post by J V on 2010-01-08
You don't need it to automount, it will mount whenever you try to open it...

You can create "symlinks" to the other part (Although for this you may indeed need to automount it lol)

Make shortcuts of folders on the other part and replace your "Pictures" folder with the shortcut, all applications will think thats a folder but actually its on the other partition.

You can edit fstab to auto mount the partition, google it for more...

---

### Post by Dj Dutchman on 2010-01-08
Thanks, found what I wanted [here]("http://www.psychocats.net/ubuntu/mountlinux") and [here]("http://www.psychocats.net/ubuntu/separatehome"). I have already done the automount one and I'm gonna take a crack at the other one in the morning. Thanks...

---

