---
title: "Virutalbox Fullscreen"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-02-06
I'm running xubuntu inside of a virtualbox. I was able to install the guest additions so I can view the box in fullscreen and it was working fine. But when I shut down and turned it on again, I can't go full screen anymore. Do I have to install the guest additions every time I restart the virtualbox?

---

### Post by jimmy the saint on 2009-02-06
you shouldn't.  Did you install Xubuntu in the virtual machine, or are you booting into a livecd image?  Do you mean that you can't resize the window, or that there is just a bunch of empty space when resize the window?  

Does mouse integration work?  if you click on the virtual machine, does your mouse only work in the virtual machine until you hit the right control key?  If that happens, the guest additions are defintely not working.

---

### Post by Sup3r3g0 on 2009-02-06
I installed it onto the virtual machine, I'm not booting from a live cd, I do have a bunch of empty space when I resize the window, I believe that mouse integration is working, and I don't have to press right control for the mouse to work.

Thanks for your help.

---

### Post by jimmy the saint on 2009-02-06
What system is your host system running?

---

### Post by Sup3r3g0 on 2009-02-06
My host is Windows XP Home.

---

### Post by Sup3r3g0 on 2009-02-06
Okay I fixed the problem. All I had to do was mess with the window compositor.

---

### Post by juanoleso on 2009-02-06
just fyi, if the kernel gets upgraded for your xubuntu guest then you will have to reinstall the guest additions.

---

