---
title: "Install Ubuntu in Virtual Box, Anything!!!"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-01-14
I am trying to install Ubuntu 9.10 in Virtual Box, but it keeps saying it needs a x64 bit kernel or something. My Windows Vista is 64-bit. How can I install it? I really want to install Ubuntu 9.10 inside a virtual machine. I'll download a 32-bit Ubuntu 9.10 if I have to. Any help? Thanks!!!

---

### Post by Cheesemill on 2010-01-14
You can only install 64-bit Ubuntu in Virtualbox if your processor and motherboard support VT-x extensions and if you have enabled then in both your BIOS and VirtualBox.

32-bit will work fine.

---

### Post by studmf on 2010-01-14
Even if the Bios/board support Vt-x, your processor has to as well.  My Guest OS in VB will not run 64X because Intel Core 2 Duo P7450 does not support it; my BIOS does.  Check your processors support on their respective manufaturer sites.  I ended up placing 32 bit Win7 and am actually glad I had to go that route so I didn't eat up as much memory.

---

### Post by UnknownFear on 2010-01-14
Would a 32x Ubuntu work? I really want to virtual-boot Ubuntu.

---

### Post by snowpine on 2010-01-14
32 bit Ubuntu should work fine in VirtualBox, good luck!

---

### Post by UnknownFear on 2010-01-14
@snowpine: Works perfectly! Installing Ubuntu 9.10 in Virtual Box :)

---

