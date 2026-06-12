---
title: "how to make partitions?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by lee_09 on 2009-09-24
what command should i type in the terminal, to make partitions on a flash drive

---

### Post by mikewhatever on 2009-09-24
The command is mkfs, if you insist on using the CLI. You can also use a graphical program such as Gparted, much easier and use friendlier.

---

### Post by Darkwing-Duck on 2009-09-29
I think that gparted will be the best for you.

```
sudo apt-get install gparted
```

Once it is installed open it up and you will see a drop down menu in the upper right. Pick the media you want to control. At the top you will see what looks like a graph. Right click > unmount

Now you can play with the partition.

Good luck.

---

### Post by Ozitraveller on 2009-09-29
You can also use fdisk

[http://manpages.ubuntu.com/manpages/jaunty/man8/fdisk.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/fdisk.8.html)

---

### Post by fuzzyk.k on 2009-09-29
fdisk is one of the easiest CLI tools for partitioning

---

