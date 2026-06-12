---
title: "Linux is saying i only have 7 mb free on hard drive"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-20
i have a 250 GB ATA hard drive...

im trying to download a file that is roughly 1.6 GB...

Ktorrent is reporting that i have only 7.6mb free...

when i open the disk usage analyzer, it says that total system capacity is 226.3 GB.. it also says that 214.8 GB is used and 11 GB is free.. when i scan the folders it says my "/" folder is 22 GB and i have 11 GB free..

in device manager i looked up the hard drive and it says its a 250GB hard drive..

what the hell is going on?

running 8.10 intrepid ibex

---

### Post by Dougie187 on 2009-04-20
Can you post the output of 
```
df -h
```

If you have a seperate home partition, you might be trying to save on a partition where you really don't have much space.

---

### Post by MaindotC on 2009-04-20
It depends on what folder you're trying to download the file.  Your partitions have quotas - set sizes that they can be.  You can change these quotas, but until you do the operating system doesn't shrink or expand them.  I'm betting you're downloading the files somewhere in your /home directory.  Download them to a different location or make a folder in / called "Downloads" and set your own permissions on it.

---

### Post by ayastona on 2009-04-20
how do i just change the size of my home partition/folder? i dont wanna move the files i just want my user to have more space..

---

### Post by Dougie187 on 2009-04-21
Can you paste the output of the command I gave you?

You have to type it into a terminal. That will tell us what you should do. Because if you don't need to, then don't change your partition sizes. You might just be saving your file on a partition that really is out of space, so you would just have to save it somewhere else.

---

