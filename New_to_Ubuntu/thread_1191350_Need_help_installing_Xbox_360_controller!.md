---
title: "Need help installing Xbox 360 controller!"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Rigorous on 2009-06-18
I'm reading a guide made by grumbel and im stuck on the attached (.txt attached below) parts.

When i put this into the terminal "scons" i get this error:  *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 817, in _main

So i ignored that and moved on then i put this in:
sal@sal-desktop:~$ sudo modprobe uinput
[sudo] password for sal: 
sal@sal-desktop:~$ rmmod xpad
ERROR: Removing 'xpad': Operation not permitted
sal@sal-desktop:~$ modprobe uinput
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save.1: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
sal@sal-desktop:~$ modprobe joydev
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save.1: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
sal@sal-desktop:~$ 


These are all the errors i get trying to follow this guide :(

---

### Post by Rigorous on 2009-06-18
Help please :(

---

### Post by Mauler5858 on 2009-06-19
You probably need to be using sudo before issuing the commands you are getting denied for.

---

