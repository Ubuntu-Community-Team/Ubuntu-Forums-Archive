---
title: "Virtulization Question"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by vault55 on 2009-12-03
[SIZE=3]For those that have experience with VMware, I need help.  I have a corporate copy of Workstation 6 (which cost a few hundred) but ESXI is free from VMware.  Whats the difference between them?

I figured 6 would be better due to the cost but its outdated. Thanks for any help or insight you can provide.:KS[/SIZE]

---

### Post by Fire_Chief on 2009-12-03
Well the most obvious difference is that ESXi is a standalone system much like a windows or standard linux install (takes over the whole drive and does not run inside another OS). Whereas VMware Workstation specifically runs inside another OS (Windows, OS X, etc.) and cannot boot on its own.

Also, ESXi can be finicky about the hardware you install it on to run. It is managed through a web interface or by using the VMWare Virtual Infrastructure Client. VMware workstation has a GUI management interface (again since it runs inside another OS).

Other questions?

Cheers!

---

### Post by vault55 on 2009-12-04
> **Fire_Chief said:**
> Well the most obvious difference is that ESXi is a standalone system much like a windows or standard linux install (takes over the whole drive and does not run inside another OS). Whereas VMware Workstation specifically runs inside another OS (Windows, OS X, etc.) and cannot boot on its own.

Also, ESXi can be finicky about the hardware you install it on to run. It is managed through a web interface or by using the VMWare Virtual Infrastructure Client. VMware workstation has a GUI management interface (again since it runs inside another OS).

Other questions?

Cheers!


Thank you Fire Chief, that was my only inquiry and you provided a textbook easy explanation. Again, I appreciate it more than you know.  I spent hours googling looking for the answer before turning to the forums.

---

