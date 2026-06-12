---
title: "boot up says my home/daniel folder does not seem to exist"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-29
That is the message I get. I booted into recovery mode and can change into both directories. 
```
ls -l
```
says I own the directories. Any ideas? 

[COLOR="White"]aa[/COLOR]

---

### Post by cmnorton on 2009-01-30
Please post the output of:

df 

sudo ls -l /home

ls -ld /home/daniel

---

### Post by Lostin60's on 2009-01-30
> **cmnorton said:**
> Please post the output of:

df 

sudo ls -l /home

ls -ld /home/daniel

I got it fixed. It actually turned out to be caused by Windows. Thanks for the reply though.
[COLOR="White"]aa[/COLOR]

---

### Post by cmnorton on 2009-01-31
How did you fix it?

---

