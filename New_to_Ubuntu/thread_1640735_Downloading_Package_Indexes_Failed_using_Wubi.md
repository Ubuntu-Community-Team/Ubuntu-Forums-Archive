---
title: "Downloading Package Indexes Failed using Wubi"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by speed86 on 2010-12-08
I installed Ubuntu 10.10 on windows using wubi but have the flowing problems:


After installing Ubuntu when I go to System>administration>drivers
I get the following:

Downloading package indexes failed please check your network status,most drivers will not be available .



Because of this I cant enable wireless to get Access to the net on Ubuntu what shouid I do?

---

### Post by Hippytaff on 2010-12-08
Plug into ethernet and try again, ubuntu gets the drivers online :-)

---

### Post by speed86 on 2010-12-08
> **Hippytaff said:**
> Plug into ethernet and try again, ubuntu gets the drivers online :-)

Yep That worked perfectly Thanks a lot!!!!!!!!!

---

### Post by Hippytaff on 2010-12-08
Excellent - remember to mark your thread as solved in the thread tools near the top of the page so others with the same problem can see how you solved it :-)

---

### Post by SebSmith on 2011-02-27
mine doesnt work even when plugged in to ethernet. solutions?

---

### Post by Hippytaff on 2011-02-28
Try going to System -> Adminstration -> additional drivers (whilst plugged in via ethernet)

---

### Post by Sxooter on 2011-07-17
I'm getting the same problem, on ethernet connection.  Weird thing is it worked with a Unetbootin 10.10 USB key, but after installing from the USB drive, it no longer works.

---

### Post by westie457 on 2011-07-17
> **Sxooter said:**
> I'm getting the same problem, on ethernet connection.  Weird thing is it worked with a Unetbootin 10.10 USB key, but after installing from the USB drive, it no longer works.

In a terminal run ```
lspci -vnn
``` then copy. Come back here and in a new reply paste the output in # tags.

---

