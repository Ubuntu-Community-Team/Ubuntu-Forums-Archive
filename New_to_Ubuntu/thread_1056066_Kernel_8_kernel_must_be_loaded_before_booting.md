---
title: "Kernel 8: kernel must be loaded before booting"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by wiredpirate on 2009-01-31
Have been running Ubuntu 8.10 for about 2 months, dual boot w/ Windows XP on my Dell Inspiron laptop.  Everything was working great until..

Battery died on laptop and ever since when trying to boot Ubuntu receive the error: 

Kernel 8: kernel must be loaded before booting

I am very new to Linux and haven't been able to find a fix that worked browsing the forums/net and have important files on the computer that I need to access.

tyvm

---

### Post by Elfy on 2009-01-31
Hi can you boot your livecd so we can get a look at your menu.lst please

Run this command

```
sudo fdisk -l
```

One of the lines, at least, will say Linux at the end - it'll look similar to /dev/sda3 - whatever yours is replace sdxy below with that.

Now run these
```
sudo mkdir /mnt/tst
sudo mount -t ext3 /dev/sdxy /mnt/tst
```

As long as you got no error run this and paste the outputs, if you got error - what was it

```
cat /mnt/tst/boot/grub/menu.lst
ls /mnt/tst/boot
```

---

### Post by ububiginner on 2010-03-17
hi hi I like to jump in this one.

after running
code:[sudo mkdir /mnt/tst
sudo mount -t ext3 /dev/sdxy /mnt/tst]

I got following error:
[mount: special device /dev/sdxy does not exist
]

What should I do?

---

