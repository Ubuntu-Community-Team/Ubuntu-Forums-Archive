---
title: "Ubuntu won't boot"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by tophatandy on 2010-08-08
So whenever I turn my system on it hangs at the ubuntu loading screen. If I press escape it says "Checking battery state" and never loads unless I go manually restart gdm. I am now missing my battery icon indicating percent of battery left as well as the sound manager. Any suggestions?

---

### Post by Rubi1200 on 2010-08-08
What are your system specs.? We need to know about RAM, disk capacity, and graphics card especially.

Thanks.

---

### Post by tophatandy on 2010-08-08
Sorry. I have an Asus Eee PC 1005ha. 
Intel Atom Proc
1 Gig Ram
Integrated Intel GMA 900 Graphics
160 Gig HD (partitioned right down the middle with windows xp)
I am running ubuntu 10.04

---

### Post by sandyd on 2010-08-08
have you tried adding "acpi=off" to the boot parameters?

---

### Post by tophatandy on 2010-08-09
> **carlee said:**
> have you tried adding "acpi=off" to the boot parameters?

no I have not. This can be done by adding that line to the end of the grub command, correct?

---

### Post by sandyd on 2010-08-09
> **tophatandy said:**
> no I have not. This can be done by adding that line to the end of the grub command, correct?

yeah. i cant remember if its either acpi=off or noacpi, but try acpi=off first

---

