---
title: "Kernel Check"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-20
I used Kernel Check to get the latest Kernel for Intrepid and my wireless don't work, I had to revert to the old Kernel. How do I remove the one Kernel Check installed?

BTW: it's 2.6.28.1

---

### Post by iaculallad on 2009-01-20
Using Synaptics: System->Administration->Synaptics Package Manager. Search for the string "linux-image" (w/o the double quote) and mark the item found as "Mark for Complete Removal" (right-click on the new kernel) and click on "Apply". That would delete the new kernel and automatically updates your GRUB entries.

---

