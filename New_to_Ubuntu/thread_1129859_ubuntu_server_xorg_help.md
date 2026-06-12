---
title: "ubuntu server xorg help"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by muted1987 on 2009-04-19
hello all that give time to help me with this as its been bugging me since i installed server version of ubuntu. 

I installed the server edition purely because i was making my own distro cd so when things go wrong it all goes back the way i like it without the hassle of all the reconfiguring, right enough gibbering to the problem.

i installed the server-restricted-modules package and then install nvidia drivers but when boot my comp i get all the way to the screen just before login which tells me 2 things 

1. (EE)Problem Parsing Config file
2. (EE)Error Parsing Config file

i cant choose any other options apart from run ubuntu in low graphics mode and it doesnt say where to look for the error so i havnt found it.

Any help appreciated as im lost

---

### Post by JoshuaRL on 2009-04-19
Unfortunately, I believe that your issue here is that you used the server kernel.  The nVidia binary driver has a problem working on the server kernel because of an enabled option (the exact type escapes me, sorry).  Unfortunately if you want the proprietary nVidia drivers you'll need to use another kernel.

To do this the easy way, you should reinstall.  If you're wanting to go minimal, do a [minimal install from the Psycocats guide.](http://www.psychocats.net/ubuntu/minimal)

Another option is to download the kernel files yourself and put them on your machine.  That can get a little involved and has some major drawbacks.  If you like I can run you through the basic steps though.

---

### Post by muted1987 on 2009-04-19
if you could run me through putting new kernal on there that would be great only reason why i put the server edition on is so i dindt get all the rubbish that i dont use from a normal install.

---

### Post by JoshuaRL on 2009-04-19
> **muted1987 said:**
> if you could run me through putting new kernal on there that would be great only reason why i put the server edition on is so i dindt get all the rubbish that i dont use from a normal install.

Well, if that's the case I'd still suggest you do a reinstall, but use the minimal install instructions I linked you to on the earlier post.  Installing your kernel is problematic in a couple of ways.  And to be honest, I haven't done it myself.  I had an option to when having some problems recently, but decided against it.  But if you're still sure you want to, I'll run you through the steps.

---

### Post by muted1987 on 2009-04-19
i probably already know the answer to this question but i have no cds will the minimal boot file work of a dvd

i know its a waste but if it gets me where i need to get to im all ffor it.

im guessing yes

---

### Post by JoshuaRL on 2009-04-19
Yeah, shouldn't have a problem.

It'll be the least used DVD ever, but it'll work.  :p

---

### Post by muted1987 on 2009-04-19
> **JoshuaRL said:**
> Yeah, shouldn't have a problem.

It'll be the least used DVD ever, but it'll work.  :p

lol very true thanks for the help

---

