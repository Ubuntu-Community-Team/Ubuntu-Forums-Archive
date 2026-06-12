---
title: "dual boot windows files location"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-06-02
Hi
I`m dual booting ubuntu with xp and would like to access some of my files (music etc) from the xp partition from within ubuntu
how can I do this?
where are these files located?
thnaks

---

### Post by nhasian on 2009-06-02
well it depends on how you installed ubuntu.  if you used wubi to install ubuntu inside of windows, then your windows drive is in /host.

if you installed ubuntu on its own drive or partition then it should be under Places in your toolbar.

---

### Post by zeroseven0183 on 2009-06-02
It depends in what partition your Windows files are located. Your Windows files are commonly found in /host

---

### Post by mevan_snp on 2009-06-02
what is the format that your using other partion's?

---

### Post by Nixie Pixel on 2009-06-02
Usually when you are dual booting on booting to Ubuntu under Places you should see your Windows partitions as something like: 

64.0 GB Media
32.0 GB Media

Or, if you named your volumes:

XP32Home
MyVolumeB

When you click on one of these Ubuntu will mount the partition for you. In the file system this usually gets mounted under /media/disk/ or a similar directory.

---

