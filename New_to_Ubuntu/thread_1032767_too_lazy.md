---
title: "too lazy"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by tctctctc on 2009-01-06
hello 
i install ubuntu 8.10 on my pc amd sempron 2,8ghz 512mb ram 80gb hdd
but my CPU work 30% up and don't down.why my machine is too lazy ?
my ram is 47% used.
thank you

---

### Post by Raynman37 on 2009-01-06
Put this into your terminal and post results here:

```
name@computer:~$ top
```

---

### Post by Michael.Godawski on 2009-01-06
> **tctctctc said:**
> hello 
i install ubuntu 8.10 on my pc amd sempron 2,8ghz 512mb ram 80gb hdd
but my CPU work 30% up and don't down.why my machine is too lazy ?
my ram is 47% used.
thank you

hi,

what is your problem exactly? 
Is your machine running too slow?

Can you please specify what you want to change?

---

### Post by bump_ on 2009-01-06
Open a terminal and type

```
top
```

This will show what programs are using the most cpu at any given moment. To see what programs are using the most memory type 'M' without the quotes and it will sort by memory usage. Type 'P' to get back to sort by %cpu usage.

---

### Post by aktiwers on 2009-01-06
Try go to System => System Monitor
See what app is using that much CPU.

Maybe it is Tracker. Thats an app that indexes your files so you can seach them like in Spotlight on OSX.

I always disable this and you can stop it from startup in System=>Preferences=>Sessions 
and untick anything that has to do with Tracker in there.

---

### Post by tctctctc on 2009-01-06
when i write top on console i see user:martin 
PID:
13456 skype                CPU - 1,7    Mem 8
16785 fire fox             CPU - 6,4    mem 17,1
3452 audio                 CPU - 1,4    mem 3

---

