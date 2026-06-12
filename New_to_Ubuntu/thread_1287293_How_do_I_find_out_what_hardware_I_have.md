---
title: "How do I find out what hardware I have"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by ConXtionS on 2009-10-10
Hi

I see all these posts where the guys have their hardware all spelled out nice and neat.

How do you do that???

is there a command or something I can type?

thanks

Jim

---

### Post by sahabcse on 2009-10-10
cat /proc/cpuinfo

---

### Post by ConXtionS on 2009-10-10
thank you sir

let me try that so my next question doesnt seem so stupid

---

### Post by damis648 on 2009-10-10
Easiest way is by using
```
lshw
```
or
```
sudo lshw
```

---

### Post by Eisenwinter on 2009-10-10
For memory info:

```
cat /proc/meminfo
```

To see how much memory is currently used:

```
free -m
```

For hard drives and partitions info:

```
df -h
```

Hope this helps you!

:)

---

### Post by ConXtionS on 2009-10-10
sweet.. thank you

---

### Post by karthick87 on 2010-04-12
```
sudo dmidecode
```

---

### Post by e4uforums on 2010-04-12
Find your newegg reciept...  :)

You can get a good simple look at things by going to System>Administration>System Monitor.  Click through these tabs and you'll get some basic info on your CPU, MEM, and HDD.

---

### Post by Son of William on 2010-04-12
e4uforums is correct.  System>Administration>System Monitor is the easiest way to quickly and conveniently locate all your basic system data.

---

### Post by hackb0y294 on 2010-04-12
Look inside, man!  That's the best way in my opinion.

---

### Post by philinux on 2010-04-12
Instal the package hardinfo from synaptic or

sudo apt-get install hardinfo

it appears under apps- system tools.

---

### Post by aysiu on 2010-04-12
I usually use ```
lspci -v
```

---

### Post by agnes on 2010-04-12
Most times I use gtk-lshw.

---

### Post by sisco311 on 2010-04-12
+1 for hardinfo. sysinfo is good too.

---

### Post by Steven_S on 2010-04-12
All of a sudden, opening up the box and writing down all the information on the different labels seems infinitely silly... 

At least I got rid of some dust bunnies in the process - I bet you can't do *that* from the command line! :biggrin:

---

