---
title: "PC speaker still works (when putting notebook to sleep) after disabling"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by bodzasfanta on 2009-08-17
I've disabled the PC speaker and system beep (which was really annoying) on my notebook in the terminal:
```
sudo rmmod pcspkr
gedit /etc/modprobe.d/blacklist
```
and added at the end of the file:
```
blacklist pcspkr
```
It stopped working when I shutdown and restart my notebook (and thats what I want) but still works if I put it to sleep (suspend).
Whats the problem?

This is an IBM Thinkpad X40

---

