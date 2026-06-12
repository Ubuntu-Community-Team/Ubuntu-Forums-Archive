---
title: "[SOLVED] Init 1 wont work"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by tropdoug on 2008-12-30
Recently installed 8.10 Kubuntu 64 amd OS, all going well, except that it won't drop into single user mode. I type in sudo init 1 in the terminal, the screen blanks out, the kubuntu bar winds up, and sticks at the last little bit, nothing happens. I hit F12 and return to normal log in screen, where I cannot select single user. 

I need to use single user to migrate my /home directory to a new hard drive. 

Anyone got any ideas?

Doug

---

### Post by snova on 2008-12-30
> **tropdoug said:**
> I need to use single user to migrate my /home directory to a new hard drive.

Reboot, and before Grub chooses the default, press the escape key. Select the "recovery mode" option and when the menu comes up, choose "drop to root shell".

Or something like that. It should suffice...

---

### Post by tropdoug on 2008-12-31
Thanks Snova

---

