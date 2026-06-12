---
title: "[SOLVED] Disk Utilization Stats"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Kissell on 2008-12-31
When I go into SYSTEM MONITOR i can see cool stat graphs on the RESOURCES tab.

These include CPU History, Memory and Swap History, and Network History. 

But I also want to see History graphs and stats on individually mounted partitions...  like, if how fast it's reading from partition /dev/sda1 and how fast it's writing to /dev/md0...  

I dunno why...  I just like graphs.

---

### Post by pdtpatrick on 2008-12-31
check out iostats 

run "man iostats" to learn about it.

---

### Post by Kissell on 2008-12-31
cool


You can install "iostat" with 

> apt-get install sysstat

Thanks!

---

