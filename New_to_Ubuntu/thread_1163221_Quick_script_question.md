---
title: "Quick script question"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Dark006 on 2009-05-18
This should be a quick one, I just need to know how to extract a number from the output of a command. Its for a script that I'll be writing soon and I've never had to do this so I'm kinda clueless on it.

The variable is:
```
ps=$(ps -C rythmbox | ??? )
```
and what I would like the "ps" variable to just display the process of rhythmbox. I've been experimenting with **cut**, **tr**, **sed**, and **awk** but I'm not sure which to use. Any suggestions?

---

### Post by Dark006 on 2009-05-18
I just figured it out. All I had to do was this 
```
ps -C rhythmbox | grep rhythmbox | awk '{print $1}'
```
Theres probably an easier way to do it though..

---

