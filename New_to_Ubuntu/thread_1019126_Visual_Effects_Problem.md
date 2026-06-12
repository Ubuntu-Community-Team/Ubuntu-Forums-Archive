---
title: "Visual Effects Problem"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by shaberl on 2008-12-22
I recently started using Ubuntu and everything so far has seemed pretty good. Except for one small problem. When i go to the Appearance Preferences and go to the Visual Effects tab, it is set to None. When i try to change it to Normal, it says "Desktop effects could not be enabled". 

Any ideas on how i could fix this? 
Any help would be appreciated.

---

### Post by nhasian on 2008-12-22
what kind of display adaptor do you have?

```
lshw -C display
```

do you have any drivers you need to enable in System->Administration->Hardware Drivers ?

---

### Post by shaberl on 2008-12-22
should i just copy what it says once i've typed in "lshw -C display"?

and there are no drivers listed under Hardware Drivers.

---

### Post by jimmy the saint on 2008-12-22
yes, let us know what the output says.

---

### Post by shaberl on 2008-12-22
ok, it says:

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by jimmy the saint on 2008-12-22
That integrated graphics chip does not seem to support compiz or 3D acceleration.

---

### Post by Miljet on 2008-12-22
Jimmy

How did you know that? Is there a list somewhere of supported chip sets?

---

### Post by shaberl on 2008-12-22
So does that mean that i can't get the Visual Effects to work at all?

---

