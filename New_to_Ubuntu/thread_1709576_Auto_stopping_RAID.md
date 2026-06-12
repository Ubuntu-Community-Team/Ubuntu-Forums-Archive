---
title: "Auto stopping RAID"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by kimdlanor on 2011-03-18
Hi,

I have setup a RAID6 array on ubuntu 10.04 LST Lucid and got it to auto start. Do I need to auto stop the array at shutdown?

I cannot find any documentation about auto stopping an array, besides the note that "mdadm --stop should typically go in a shutdown script. I started looking for the reason why the array does auto start, but could not find anything more than an "auto=yes" in /etc/mdadm/mdadm.conf.

So the question is how does the array auto start? How do I get it to auto stop? And is adding a mount-point in /etc/fstab enough for auto starting and auto stopping?

Thanks in advance,

---

