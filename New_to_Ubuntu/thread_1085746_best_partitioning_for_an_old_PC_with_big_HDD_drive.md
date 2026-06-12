---
title: "best partitioning for an old PC with big HDD drive"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by pjstock on 2009-03-03
I am installing Ubuntu 8.10 on an oldish PC but with a new largeish (250gb) hard drive.
My first attempt (using the entire drive as a single partition) ended in an Error 18 (which I now understand meant the old bios couldn't handle such a large drive.)

back to square one and a reinstall, I choose the Guided Partitioning  with a default small partition up front. 

Everything worked smoothly except, on restarting it seems that I only have 207Gb of hard drive free. It seems that I have lost a fair chunk in the storage capacity.

Can anyone suggest a better approach? I tried to go the Manual Partition route, but even reading the documentation, I couldn't figure out the optimal sizes and Use As choices. 

Can I repartition more optimally without reinstalling Ubuntu (though that is a pretty quick process and so would not be a great hassle.)

Many thanks

Peter

---

### Post by cwsnyder on 2009-03-03
I think the part of your problem which is the 'disappearing disk space' is the old, old problem that hard drive manufacturers list the amount of storage space in millions or billions of bytes, while your operating system reports the storage space in MB (1048576 bytes = 1024 squared bytes =1 MB) or GB (10737741824 bytes = 1024 cubed bytes = 1 GB).

As for the partitioning, standard practice would have a 10G  root ( / ) partition, a Swap partition which is the smaller of 512M or twice your RAM memory size, and use the rest of your drive as either a large /home partition, or add the server standard extras: /usr, /bin, /sbin, /etc and a few others.  I am a relative n00b, so I wouldn't attempt to specify relative sizes.  I do keep a separate /home partition, because it simplifies operating system updates.

---

### Post by Michael.Godawski on 2009-03-03
Agreed. 
Have a look here:


[LIST]
[*][http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[*][http://ubunturesources.ub.ohost.de/ubuntuinstall.html](http://ubunturesources.ub.ohost.de/ubuntuinstall.html)
[/LIST]

---

### Post by swoody on 2009-03-03
Hi pjstock! And welcome to Ubuntu and the Forums!! ):P

> **cwsnyder said:**
> standard practice would have a 10GB  root ( / ) partition, a Swap partition which is the smaller of 512M or twice your RAM memory size, and use the rest of your drive as either a large /home partition... keep a separate /home partition, because it simplifies operating system updates.

I would agree with this 100% It makes updates a lot easier and hassle-free, while not having to go crazy with partitions. This is the same setup I've been using for every install I've done, and it has made life much easier :D

---

### Post by pjstock on 2009-03-04
Thanks Michael.

These links looked very helpful, but when I tried to follow along, I got kind of lost. 

For instance, when I got to the Partitioner, the first Guided option only offered me two partitions. It wouldn't allow me a Swap partition.

So I tried the Manual route and tried to set up:
- a 10000Mb partition 1 for the root system (I guessed at Primary, and ext3 file system.
- a 239001 MB partition 2 (Primary, ext3) for general use.
- a 254mb swap partition.

On restarting I got an error that the Greeter could not be found and that just kept coming up over and over.

the large middle partition (do the colours actually indicate anything?) had "Ubuntu 8.10" marked in it, so I am not sure if the system files wound up on the large general storage area or not.

so far none of the Docs or tutorials seem to match the way my Partitioner is looking and working.

in the end I started over again and just used the Guided partitioning, and let it set itself up. I don't think there is a swap partition now. 

> **Michael.Godawski said:**
> Agreed. 
Have a look here:


[LIST]
[*][http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[*][http://ubunturesources.ub.ohost.de/ubuntuinstall.html](http://ubunturesources.ub.ohost.de/ubuntuinstall.html)
[/LIST]

---

### Post by ikisham on 2009-03-04
Actually the guided partitioning installs everything in '/' and creates a swap partition too, I think.

---

