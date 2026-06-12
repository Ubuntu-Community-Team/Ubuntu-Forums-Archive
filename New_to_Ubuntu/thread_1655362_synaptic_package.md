---
title: "synaptic package"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by magedsoft on 2010-12-29
hay all : 
 

my friends Tom Download all package in synaptic and i want to make copy of them and use it how i make them useful to me 



thank u

---

### Post by howefield on 2010-12-29
Downloaded packages will be stored in /var/cache/apt/archives from where they can be copied to an external drive.

You can then paste them into the same folder on your computer. You'll need to use elevated rights to paste them into the folder eg, from terminal

```
sudo cp <path to files> /var/cache/apt/archives
```

Synaptic will see them and use them instead of downloading them.

---

### Post by magedsoft on 2010-12-29
thank u too much 

how to classify them or know what i need from them i see that big number of files 
and i don't know them in windows i know that k-lite or winamp for audio and video 
but in linux i don't know the right package for every thing 

how i can classify them ??? 


thank u again

---

