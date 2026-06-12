---
title: "printer driver"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by jwalters on 2011-01-14
Hi . . . . just purchased an HP deskjet 2050 printer. Does anyone know how to install a driver for this thing. I did all the regular stuff, but it seems I need a generic one.

I downloaded a generic driver to my desk top, but can't get it to open.....help?

I'm Ubuntu 10.04

---

### Post by Frogs Hair on 2011-01-14
Hi,

What do mean by regular stuff ? I have a different model of HP printer . I installed by Connecting the printer and going to System > Administration > Printing.

I selected add from the dialog box and Ubuntu located the printer and searched for a driver . After the driver installed I was offered a test print.

If the driver is for windows that would explain why you can't open it.

---

### Post by hansolo4949 on 2011-01-14
Yes, you should do what frogs hair said. If that doesn't work, you should install the windows driver via ndiswapper (sudo apt-get install ndiswapper, or search for it in the software center).

That should work!

hansolo4949

---

