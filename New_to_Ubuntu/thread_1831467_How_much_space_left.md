---
title: "How much space left"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by BlackoutWorm on 2011-08-23
Hey. I'm using ubuntu 11.10, and I really like it.
Installed it the other day after I have now been using wubi fro about a month now.
But I have a question.
In Windows, i can easily see how much space there is left and used on each of my disks. How do I check the size here in ubuntu?
I tried to view the files in list with details but the size doesn't say anything at all.
I assume that's one of these bugs I've heard of. You know, when they say windows has viruses and linux has bugs.
So, how do I fix that bug, and is there a way I can see the size used and left?

---

### Post by raja.genupula on 2011-08-23
```
df -h
```
gonna provide you everything about space

---

### Post by sanderd17 on 2011-08-23
wubi is always a bit weird (the filesystem used by wubi is seen as a single file by windows, so that could give problems). But you could try the app "baobab". It should be installed under a name like "disk space viewer" or something similar, but if you don't find it, just press ALT+F and execute "baobab" (without quotes) or type baobab in the unity search thingy.

---

### Post by haqking on 2011-08-23
> **BlackoutWorm said:**
> Hey. I'm using ubuntu 11.10, and I really like it.
Installed it the other day after I have now been using wubi fro about a month now.
But I have a question.
In Windows, i can easily see how much space there is left and used on each of my disks. How do I check the size here in ubuntu?
I tried to view the files in list with details but the size doesn't say anything at all.
I assume that's one of these bugs I've heard of. You know, when they say windows has viruses and linux has bugs.
So, how do I fix that bug, and is there a way I can see the size used and left?


df -h

or if you want a GUI then system>administration>system monitor then choose file systems tab

---

### Post by BlackoutWorm on 2011-08-23
Thanks a lot guys.
I love ubuntu. There are like 10 different ways to do things:)
Is there a way I can make it show the data from baobab either in the Computer folder or the sidebar, below or next to the disk name?
Not a big deal but I'm just used to see the size there.

---

### Post by raja.genupula on 2011-08-23
> **BlackoutWorm said:**
> Thanks a lot guys.
I love ubuntu. There are like 10 different ways to do things:)
Is there a way I can make it show the data from baobab either in the Computer folder or the sidebar, below or next to the disk name?
Not a big deal but I'm just used to see the size there.
i know about terminal man . in terminal you have to give as this by cd to that folder 

```
du -h 
``` gives each file in that folder and last line is its total size  . 
```
du -h | tail -n1  
``` only total size , not gives individual size .

---

