---
title: "ACPI and QUIET???"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by fslezak on 2010-03-04
Hello. I recently put ACPI support on my laptop using acpi=force .

However, when I put quiet in the arguments, I lose the ACPI. I also use pci=noacpi .

The standard is below. The ACPI is in red. Where should I put the "quiet" statement?

```
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=ad417012-5aaf-4f56-92f6-4b4b5156ee59 ro [COLOR=Red]acpi=force pci=noacpi[/COLOR] splash 
```

---

### Post by jim Kane on 2010-03-04
> **fslezak said:**
> Hello. I recently put ACPI support on my laptop using acpi=force .

However, when I put quiet in the arguments, I lose the ACPI. I also use pci=noacpi .

The standard is below. The ACPI is in red. Where should I put the "quiet" statement?

```
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=ad417012-5aaf-4f56-92f6-4b4b5156ee59 ro [COLOR=Red]acpi=force pci=noacpi[/COLOR] splash 
```

&#65279;
acpi=force pci=noacpi should go after "splash" on the same line

well thats how i use acpi=force apm=power_off so i should think it will work ok.

JK

---

### Post by fslezak on 2010-04-05
Where does the QUIET statement go?

---

