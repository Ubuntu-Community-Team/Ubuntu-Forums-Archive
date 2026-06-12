---
title: "System beep"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by rick astley on 2009-04-13
how can i permanently disable that horrid system beep that comes from the pc speaker. through the terminal.


thanks,
rick

---

### Post by skymera on 2009-04-13
I think it's this:

```
 sudo rmmod pcspkr 
```
If it works to keep it permaent do this:

```
 sudo echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist 
```
I love my system beep :)

---

### Post by rick astley on 2009-04-13
excellent. greatly appreciated

---

### Post by txwooley on 2009-04-13
> **skymera said:**
> I think it's this:

```
 sudo rmmod pcspkr 
```
If it works to keep it permaent do this:

```
 sudo echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist 
```
I love my system beep :)

Won't that disable the pc speaker for all apps?  I get odd system beeps too but haven't narrowed down their exact source yet, but i do want to use my speakers for movies and such!

---

### Post by skymera on 2009-04-13
This is system speaker, not sound stereo speakers. Totally different.
pcspkr module doesn't affect sound in any way.

---

### Post by steve101101 on 2009-04-13
also you can do it graphically by ...
system > preferences > sound then click on the sound tab.

---

