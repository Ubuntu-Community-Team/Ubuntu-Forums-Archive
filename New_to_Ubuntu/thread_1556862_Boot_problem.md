---
title: "Boot problem"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by jm951 on 2010-08-20
Was on the internet last night on my desktop which is set up with a dual boot for Vista and Ubuntu 9.1? when the power went out. Now Vista won't reboot at all. Ubuntu won't boot either. The message I get on Ubuntu-

GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions.]
sh:grub>

Sorry to bother anyone if this is a very simple problem, but I'm still pretty new to the Ubuntu world. I need to get this system back up and running pretty quickly, at least in Ubuntu. I'll solve the Vista problems later.

tia

---

### Post by Peter09 on 2010-08-20
can you type
 
```
ls
```
at the grub prompt - it should show a list of bootable systems. I am not an expert on grub, there is also the issue of whether you are running Grub or Grub 2. Here is more detailed documentation on Grub2, including some details of rescue mode.
 
 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by jtarin on 2010-08-20
[Grub documentation to help you boot.]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

---

