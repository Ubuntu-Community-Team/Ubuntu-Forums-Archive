---
title: "HDD access time check"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by mbzn on 2009-12-20
Hi, I need a decent program that i can use to compare disk access time between my SCSI raid and my SATA raid and would be a bonus if it can work on different file systems.

A timer together with cp could work but i would like a graph, sort of like 'nero drivespeed'

Thanks

---

### Post by pbrane on 2009-12-20
Have a look at hdparm. *man hdparm* in a terminal will access the man page.

```

hdparm -t /dev/<drive to test>

```

performs timings.

---

### Post by mbzn on 2009-12-20
Thanks, looks fine, I know the man page tells me this but what is the switch to change the default 54MB so i could make a graph?

Thanks again

---

### Post by pbrane on 2009-12-20
I'm not sure what you mean by 'default 54MB'. I guess what you want is to run the test for a length of time and get date points at certain intervals to plot a graph of the disc performance. I don't know how or even if you can do that with hdparm. Other that writing a shell script.

---

