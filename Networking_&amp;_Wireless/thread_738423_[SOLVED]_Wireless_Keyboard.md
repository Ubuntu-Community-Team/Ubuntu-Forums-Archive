---
title: "[SOLVED] Wireless Keyboard"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by bioShark on 2008-03-28
Hi 

I have just bought a keyboard + mous combo. Logitech Wave keyboard and Logitech LX8 mouse. 
Both work perfectly, but Logitech didn't bother creating a software for Linux as well. So I can't set up all the nice features they have. 
Anyway, that's my smallest problem :). The real problem is that I use bual boot. Ubuntu/WinXP. Now, when I start the PC, the keyboard is recognized because I can go into BIOS without any problem, but when I get to boot loader (Grub), I can't choose anything, so I am stuck with the first option (Ubuntu). But...I would like to boot from WinXP as well. So, the keyboard is dead in the watter when I am in Grub.

Any solution on how to make my boot loader recognize my keyboard?

Thanks in advance.

c.u.

---

### Post by bioShark on 2008-03-29
Come on guys...no solutions?

---

### Post by realmatt on 2008-03-30
You should turn on USB emulation in your BIOS.  There are no USB keyboard drivers loaded during the time grub is running.  USB emulation treats it like a PS/2 keyboard so far as the software is concerned.

---

### Post by bioShark on 2008-03-30
Hi

Thx, I will try that. Although this PC is pretty old, I hope I have an option like "USB emulation" in my BIOS. It's strange though that I can get into BIOS with this keyboard.

I'll get back to you if it works.

---

### Post by bioShark on 2008-03-30
Hi

Thx, it worked. It's called: USB keyboard support enable/diasable.


thx, again.

---

