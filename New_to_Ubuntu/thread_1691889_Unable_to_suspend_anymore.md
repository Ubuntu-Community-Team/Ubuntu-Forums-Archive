---
title: "Unable to suspend anymore"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by leviathan8 on 2011-02-20
Hi, I'm using Ubuntu 10.04 on a Dell N5010 laptop. Recently, I installed openssh-server and restarted the CUPS server in order to connect to my printer on network. However, after I did this, I am unable to suspend anymore. When I press the suspend button, the screen freezes a while and comes back to its state after a short while. When closing the lid, same thing happens. However, if I close the lid 2 times consecutively, it works. Is there any way to fix this? It's really frustrating. Thanks.

---

### Post by leviathan8 on 2011-02-21
Well, I believe that it is now fixed. I've been browsing the internet for some workarounds, and I got up with a program called "s2ram" from the package "uswsusp".

> sudo apt-get install uswsusp

This program generated a new initramfs, and apparently, after a reboot, it fixed this issue. The program can also be used manually by typing 

> sudo s2ram -f

in order to suspend to ram, and

> sudo s2disk

in order to hibernate.

I have done several tests with my laptop, with and without the program, and it works for now. I hope this information is useful for anyone having this problem. If I discover new issues, I will post back, until then, I will mark the thread as solved.

---

