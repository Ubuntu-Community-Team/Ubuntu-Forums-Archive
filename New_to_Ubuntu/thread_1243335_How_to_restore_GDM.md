---
title: "How to restore GDM?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Kalonosaur on 2009-08-18
With all my ignorance firmly in hand I went to system-admin-services and removed the tick from the graphical login manager box thinking that it might get rid of the login business, but instead i got a .prompt screen and a headache. I'm sure it's easy to reverse this but keep it simple please.

---

### Post by wojox on 2009-08-18
Boot your live cd.
Open Places > Computer
Mount your partition on the left (double click)
Redo what you did.

Then when your done unmount.
reboot and open System > Admin > Login Window and set it to automatic login.

---

### Post by Kalonosaur on 2009-08-18
Hi wojox, Following your instructions doesn't seam to give me access to the system tools, just the files.

---

### Post by mcduck on 2009-08-18
Try logging in and then running "sudo /etc/init.d/gdm start". That should start GDM, allowing oyu to log in to desktop and to change the settting back again.

---

### Post by philinux on 2009-08-18
> **mcduck said:**
> Try logging in and then running "sudo /etc/init.d/gdm start". That should start GDM, allowing oyu to log in to desktop and to change the settting back again.

+1. login at the command prompt.

---

### Post by Kalonosaur on 2009-08-18
All sorted. Cheers.

---

