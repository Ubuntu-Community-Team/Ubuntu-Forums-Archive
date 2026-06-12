---
title: "Cannot create folder on secondardy drive"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by servicetech on 2009-10-29
When I go to create folder on a my secondary partition the "create folder' is greyed out. Also I cannot access the directories with programs or save to the drive on Firefox.

---

### Post by halitech on 2009-10-29
sounds like you don't have ownership of the drive you are trying to write to. Look here for more info

[http://linuxcommand.org/man_pages/chown1.html](http://linuxcommand.org/man_pages/chown1.html)

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by danastasio on 2009-10-29
> **servicetech said:**
> When I go to create folder on a my secondary partition the "create folder' is greyed out. Also I cannot access the directories with programs or save to the drive on Firefox.

it sounds like your computer doesnt think that you own the drive, if the drive is mounted at /media/disk1, and your username is john, then, in a terminal run:
```
sudo chown john /media/disk1
```

---

### Post by servicetech on 2009-10-29
I think you're right on the ownership thing, I read the pages but as a newb Still don't know what I need to do.

---

### Post by danastasio on 2009-10-31
> **servicetech said:**
> I think you're right on the ownership thing, I read the pages but as a newb Still don't know what I need to do.

Alrighty, the drive in question is internal right?

go to places>computer>(and then click on the partition that you're trying to access)

and with the window that pops up, you should be able to find the mount point of the partition in the location box (see attached screenshot.)

now you know what the partition is named as far as your computer is concerned. copy this address, the entire thing, it can be quite long.

alright, lets say your username is bob, you would then, in a terminal type

```
sudo chown bob /media/drive
```

replacing "/media/drive" with the text that you copied earlier.

You now own the drive!

---

