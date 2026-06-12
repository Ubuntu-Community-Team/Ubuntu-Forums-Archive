---
title: "hard disk speed(performance) test"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by infestor on 2009-10-10
is there a programme that you can suggest to analyse hard disk speed (performance)? i have 2 disks and suspect that one is really not doing well :(

---

### Post by SkyNet2029 on 2009-10-10
hdparm will test your hard drive throughput and allow you to modify specific parameters to fine tune your drive's performance.
 
```
$sudo apt-get install hdparm
```

---

### Post by infestor on 2009-10-10
> **SkyNet2029 said:**
> hdparm will test your hard drive throughput and allow you to modify specific parameters to fine tune your drive's performance.
 
```
$sudo apt-get install hdparm
```

can you provide me a code to run the test please?

---

### Post by Sir Jasper on 2009-10-10
Hi,

For reading speed tests try:

sudo hdparm -tT /dev/sda
and/or
sudo hdparm -tT /dev/sdb

My regards

---

