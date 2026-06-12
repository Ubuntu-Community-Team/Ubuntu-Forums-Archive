---
title: "PCI Parallel Card - Cannot install / have driver tho..."
date: 2009-10-14
forum: New to Ubuntu
---

### Post by satsiraj on 2009-10-14
i have a pci parallel card - Altomtech single parallell port on pci hooked to my mobo my mobo is a x48 intel it does not have a parallel port onboard - 

i have an epson priinter LX 300 dot matrix....

in windows i connect it under LPT3 and works fine no need to install any drivers...

under hardware manager it says - pci-com port (lpt1)  pci-com port (lpt2) pci-com port (lpt3)

i have the original driver cd but ubuntu says cannot copy that into /usr/sbin
which is the instruction on the driver cd readme... to install on linux systems...


please help...

---

### Post by elvisd on 2009-10-21
to copy to /usr/bin you need admin privileges
use sudo before your commands

i.ex.

```
sudo cp lptdriver.bin /usr/bin
```

hth

---

