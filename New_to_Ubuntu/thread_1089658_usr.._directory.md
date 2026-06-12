---
title: "usr.. directory"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-03-07
Question: I have a directory "usr.." in my root directory...
 
I see that today for the first time. I recently updated from debian lenny to debian squeeze.
 
Anybody knows whether this is a system/update file, or has my system been compromised?

---

### Post by SunnyRabbiera on 2009-03-07
It should be alright, but its not a smart idea to use the root account.

---

### Post by taurus on 2009-03-07
You mean /usr?  That's where binaries, libraries, manpage, etc. are resided.

---

### Post by WitchCraft on 2009-03-07
> **taurus said:**
> You mean /usr? That's where binaries, libraries, manpage, etc. are resided.
 
No, I mean "usr..", which is not where the binaries are.
 
> **SunnyRabbiera said:**
> 
It should be alright, but its not a smart idea to use the root account.

I know, I know... 
I hope it's allright, will have a closer look at it as soon as I boot back to Linux. Currently have to do work on the f*ing windoze, and just saw the usr.. directory when I accessed the ubuntu partition.
It might also have been the [HastaLa]Visa search indexer, which also creates random directories, but normally, these files rather look like 7df91f073c4b95475567fcd1244a

---

### Post by taurus on 2009-03-07
You mean /root/usr.  You can see if there is anything in there.

```
ls -la /root/usr
```
or 

```
sudo ls -la /root/usr
```

---

### Post by WitchCraft on 2009-03-07
> **taurus said:**
> You mean /root/usr. You can see if there is anything in there.
 
```
ls -la /root/usr
```
or 
 
```
sudo ls -la /root/usr
```
 
no i mean /usr..
 
file:///usr..

---

### Post by SunnyRabbiera on 2009-03-07
It should be fine.

---

### Post by taurus on 2009-03-07
```
ls -la /usr
```

---

### Post by WitchCraft on 2009-03-12
> **taurus said:**
> 
```

ls -la /usr

```


Further investigation showed that it's a compatibility layer for ktorrent.

---

