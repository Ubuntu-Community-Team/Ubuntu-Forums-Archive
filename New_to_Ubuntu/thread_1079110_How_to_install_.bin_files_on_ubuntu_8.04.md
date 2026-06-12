---
title: "How to install .bin files on ubuntu 8.04 ?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by negative: on 2009-02-24
Hey there, FIRST POST!@

ha, anyways, 

I am trying to install Packet Tracer "PacketTracer51_i386_installer-deb.bin" because i need it for school, but i have nfi how to install it. 
I tried going through this forum, and i couldn't find anything. 

I downloaded it to the desktop and it's just sitting there, pissing me off. 

This is the command i tried. 

************@deceased:~$ ~/Desktop$ chmod a+x PacketTracer51_i386_installer-deb.bin

and i get this error..

bash: /home/************/Desktop$: No such file or directory

lil help :D

---

### Post by iaculallad on 2009-02-24
What about doing the set of commands below, assuming you did download the BIN file on your Destkop:

```
cd ~/Desktop
sudo chmod a+x *.bin
sudo ./PacketTracer51_i386_installer-deb.bin
```

---

### Post by negative: on 2009-02-24
awesome, thanks for that :)

installed perfect
so easy haha


:P

---

### Post by vip3rousmango on 2009-10-25
when I try it I get this:

```
alexander@openGEULaptop:~$ chmod a+x AdobeAIRInstaller.bin
chmod: changing permissions of `AdobeAIRInstaller.bin': Operation not permitted
alexander@openGEULaptop:~$ 
```


it's also the same when I use sudo in front as well. I'm probably  missing something..

---

### Post by vinutux on 2009-10-25
> **negative: said:**
> awesome, thanks for that :)

installed perfect
so easy haha


:P

plz... mark thread SOLVED

---

### Post by elord on 2010-08-12
Cool now i can use packet tracer on my Ubuntu:p:p:p:p:p

---

