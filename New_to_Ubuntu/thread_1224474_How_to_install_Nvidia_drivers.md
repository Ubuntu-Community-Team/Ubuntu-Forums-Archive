---
title: "How to install Nvidia drivers?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by racie on 2009-07-27
Okay, I've had Ubuntu before, but I can't seem to figure out how to install the Nvidia drivers.  Shouldn't they be in 'Hardware Drivers'?  I feel like I'm missing something obvious.  :/  I have Jaunty by the way.

---

### Post by Arup on 2009-07-27
Unless you have nvidia or ATI, for Intel the drivers already come pre-installed.

---

### Post by philinux on 2009-07-27
> **racie said:**
> Okay, I've had Ubuntu before, but I can't seem to figure out how to install the Nvidia drivers.  Shouldn't they be in 'Hardware Drivers'?  I feel like I'm missing something obvious.  :/  I have Jaunty by the way.


It should be offered there. Try updating.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sandeepraj on 2009-07-27
goto applications-->add/remove programs
now..set to all avalible applications and search nvidia and install :
1. NVIDIA X Server Settings.
2. NVidia binary X.Org driver ('version 177' driver) [works wid most nvidia cards try other versions if needed]

---

### Post by racie on 2009-07-27
Thanks!  An update fixed it.  :D

---

### Post by sackbj on 2009-07-27
I'm switching to nvidia from ATI.  Does nvidia hvea pretty good support through getting their driver from "add/remove programs" or would a program like EnvyNG be better for automatic configuration?

---

### Post by terry_gardener on 2009-07-27
i also have nvidia cards and i use the hardware drivers from system - administration 

if it is not listed in there then i use envyng 

never tried it through add/remove or synaptic.

---

