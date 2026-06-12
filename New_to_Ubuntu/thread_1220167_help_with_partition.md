---
title: "help with partition"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by a rom on 2009-07-22
Help,  gparted looks like this,

partition                                  filesystem                    label

/dev/sda1                                   fat 16                         
/dev/sda2                                    ntfs                          recovery
/dev/sda3  [warning triangle]        ntfs                           os
/dev/sda4                                  extended

I am not able to resize the sd3  with the warning triangle, what should i do?

I am trying to install Ubuntu 8.10, its harder than i thought.

Thanks

---

### Post by nwadams on 2009-07-22
the triangle might mean that its mounted. try to right click on it and go unmount volume. that might remove the triangle.

---

### Post by superprash2003 on 2009-07-22
if that doesnt work , in the terminal type **sudo umount /dev/sda3 **to unmount

---

### Post by a rom on 2009-07-22
ok, thanks, ill try that.

---

### Post by ~sHyLoCk~ on 2009-07-22
You can also resize it during install afaik

---

### Post by mapes12 on 2009-07-23
You can't use GParted to work on active partitions i.e. where your OS is running off the HDD. That may be why you have th triangle. Load up Gparted from a GParted Live CD or the UBU Live CD (if it works - mine doesn't). And be VERY careful what you do. This newbie HowTo site may also help you get a dual boot configuration working for you: 

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

