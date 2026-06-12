---
title: "Removing Old Versions of the Linux Kernel"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by lego6245 on 2009-02-07
Ahoy again!
After updating the linux kernel, I saw that after rebooting, there were 2 options to boot from, the newer kernel, and the older kernel. How would I go about removing the older kernel from the list?

---

### Post by taurus on 2009-02-07
One way is to go into System -> Administration -> Synaptic Package Manager -> Search and type in **linux-image**.  Then, highlight and remove the one that you don't want from there.

---

### Post by x33a on 2009-02-07
other way is to edit your menu.lst file.

type gksudo gedit /boot/grub/menu.lst, 

search for the kernel, and place a # before that line and save the file.

Note: it's always better to keep at least 2 kernels on the boot menu, in case one goes bust.

---

### Post by sam_delta on 2009-02-07
you can also install startupmanager and manage your grub menu

sam

---

### Post by lego6245 on 2009-02-08
Thanks a lot for your help :P

---

### Post by stchman on 2009-02-08
> **x33a said:**
> other way is to edit your menu.lst file.

type gksudo gedit /boot/grub/menu.lst, 

search for the kernel, and place a # before that line and save the file.

Note: it's always better to keep at least 2 kernels on the boot menu, in case one goes bust.

That does not remove the kernel.

---

### Post by x33a on 2009-02-08
> **stchman said:**
> That does not remove the kernel.

he asked about removing the kernel from the list, and not from the computer.

although, the latter will automatically remove it from the list ;).

---

