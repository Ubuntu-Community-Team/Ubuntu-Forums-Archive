---
title: "Checking the size/used/free etc. for main disk?"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-13
How do I check the free space and used space on my primary hard drive where ubuntu is installed?

Instead of showing the drive as C:/ for example, it just says File System so I cant actually treat it as if it's a drive.

So how can I view the properties of my main hard drive, or get it to act like a drive...if you get what I mean?

---

### Post by SunnyRabbiera on 2009-06-13
You can see disk usage by simply using the system monitor, located under system > administration > system monitor.
It should give you space available.

---

### Post by Bucky Ball on 2009-06-13
Haha Gp ... Gp-arted! That will also give you a look at what is happening with your drives and a whole lot more.

If you haven't already got 'Partition Manager' under System->Administration, then go to Synaptic Package Manager, search for and install:

gparted

It will then appear in System->Administration. :)

---

### Post by nandemonai on 2009-06-13
Also in terminal:

```
df -h
```

But by far the best overview in my opinion is Applications -> Accessories -> Disk Usage Analyser

As a side note:

Linux treats drives differently to Windows. File systems or 'drives' are mounted into the root of your system (/).

Generally mounted file systems are mounted under /media or /mnt though you can mount anywhere.

You could, if you wished, have a separate drive for each directory in the system.

---

### Post by Bucky Ball on 2009-06-13
Thanks for the command and hi from Adelaide, SA also! :)

---

