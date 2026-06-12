---
title: "How to use safe mode boot ?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by loseby on 2011-04-07
Ubuntu wont boot , it appears just at the last part something is stopping it. Could be video drivers or something along that line. 

What happens is..

1/ You select the last Unbuntu ( system is dual boot with linux on a seperate hard drive ), well the one on top of the GRUB

2/ It goes through all these lines of code ( or whatever its called ) and then the screen goes a purple colour

3/ The it either goes to a blank screen and stays there or stays a purple type colour and stays there ...no error messages etc

Usually after purple colour Ubuntu starts

So how can I use safe mode to fix the problems....I have no real skills or knowledge of the command line


btw: in GRUB if I select the Win7 boot I have no problems

---

### Post by Paqman on 2011-04-07
Try the recovery mode (which is the second from top option) and see if you can boot into a command line. From there try
```
startx
```
and see what errors it spits out.

---

### Post by loseby on 2011-04-09
> **Paqman said:**
> Try the recovery mode (which is the second from top option) and see if you can boot into a command line. From there try
```
startx
```
and see what errors it spits out.

startx gave the same blank screen

I tried fix broken package ( I think thats what I selected ) and opted to run in low graphics mode.....short story is I am back in and the problem that I keep having seems to be with my graphics card or to be exact the advance drivers. Have had problems before and have and ended up reinstalling Ubuntu but this time I needed some data which I now have

---

### Post by Paqman on 2011-04-10
What sort of graphics card do you have, and where are you getting the drivers from?

---

