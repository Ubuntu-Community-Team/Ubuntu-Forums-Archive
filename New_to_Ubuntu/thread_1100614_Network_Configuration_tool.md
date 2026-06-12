---
title: "Network Configuration tool"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by iLeet on 2009-03-19
I'm using Ubuntu 8.10
I installed ndiswrapper
Installed my drivers **Under the name it says yes**
I rebooted my PC
I click configure network and it says > Cannot detect network configuration tool
Whats wrong?

I have wine installed and tried install Microsoft networking boardband
It didnt work.

---

### Post by iLeet on 2009-03-19
I still have the problem

---

### Post by dugh on 2009-03-19
> **iLeet said:**
> I still have the problem


Does wireless actually work?

If not, post the output of these commands (run in the Terminal):

iwconfig

ndiswrapper -l

lshw -c network

I've been having problems with wireless not working, too, after a recent upgrade:
[http://ubuntuforums.org/showthread.php?t=1100133](http://ubuntuforums.org/showthread.php?t=1100133)

Still don't have the solution.

---

