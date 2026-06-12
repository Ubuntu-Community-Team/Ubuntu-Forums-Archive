---
title: "MSI GX700 notebook, ACPI/battery status errors"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by geckoguykc on 2009-03-14
Ubuntu detects my battery status correctly for the first couple of hours of use. After that it says that the computer is running on AC power regardless of whether it actually is. The computer will not suspend or hibernate either, and the LCD brightness goes down unexpectedly for no apparent reason. I realize that this is because my manufacturer is purposefully making windows proprietary BIOSs, but I was hoping there was some workaround. I have heard that this problem is resolved by getting the computer to switch from IRQ mode to EC polling mode, but all the patches I have encountered that supposedly fix this involve the ec.c module, and all of the modules in my /lib/modules directories are labeled with the .ko extension. I can't find an ec.ko file either. 

I have found a launchpad ppa repository for a patched kernel that supposedly fixes this problem, but I'm not entirely sure how to install this kernel after I've added the repositories. 

[https://launchpad.net/~timo-tretter/+archive/ppa](https://launchpad.net/~timo-tretter/+archive/ppa)

Is there any other way to start the kernel in EC polling mode instead of IRQ mode? 

I'm using Intrepid with kernel 2.6.27-7-generic.

Is there any chance that this will be fixed in jaunty?

---

### Post by geckoguykc on 2009-03-14
Do I just use apt to get install "linux-source" or something to install the patched kernel from the repository? I've added it to sources.list and added the keys for it.

---

### Post by geckoguykc on 2009-03-14
"dmesg | grep BAT" returned several errors. 

```

casey@lappy486:~$ dmesg | grep BAT
[    1.188423] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node ffff88012fa355a0), AE_NOT_EXIST
[    1.188526] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node ffff88012fa355a0), AE_NOT_EXIST
[    1.194513] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node ffff88012fa355a0), AE_NOT_EXIST
[    1.194611] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node ffff88012fa355a0), AE_NOT_EXIST
[   19.221335] ACPI: Battery Slot [BAT1] (battery present)


```

Any ideas?

---

