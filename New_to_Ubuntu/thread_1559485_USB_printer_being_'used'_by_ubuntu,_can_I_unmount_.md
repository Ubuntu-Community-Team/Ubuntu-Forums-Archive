---
title: "USB printer being 'used' by ubuntu, can I unmount to use in virtualbox?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by jotto! on 2010-08-23
Am having a problem with my USB printer in virtualbox. I can use and access all of my other usb devices except for my printer.
I wondered if it was being 'held' by the host system and so wondered if it is possible to unmount it so that I can plug it in and it be recognised in my virtual guest.

---

### Post by silverglade00 on 2010-08-23
It might be easier to share the printer and then set your guest to use it as a shared printer.

---

### Post by jotto! on 2010-08-23
That sounds like a plan! how would I go about doing that?

---

### Post by silverglade00 on 2010-08-23
Go to System - Administration - Printing. Right-click your printer and choose Shared. Then in your guest set it up as a network printer on \\host-name-or-IP\printer-name. We need to know what your guest system is as well.

---

### Post by jotto! on 2010-08-23
Ok, the printer is already set as shared but it is not being seen in the guest OS which is Xp pro sp3. I have 3 shared folders which all seem to work and be shared ok....just cant use the printer!

---

### Post by jotto! on 2010-08-23
Ok, did some googling and managed to work it out.
I opened the cups page and ticked a box that said Share printers connected to this system. Then in the guest OS, added a network printer using a http address that corresponded to the printer address.

All good!

---

### Post by silverglade00 on 2010-08-23
Congrats! Glad you got it working. Would you mind marking this thread as solved?

---

### Post by jotto! on 2010-08-24
> **silverglade00 said:**
> Congrats! Glad you got it working. Would you mind marking this thread as solved?

No problem!

---

