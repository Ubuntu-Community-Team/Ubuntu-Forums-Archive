---
title: "PAE Kernel Issues"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by purpleacid on 2011-07-01
I recently added some RAM to my PC, pushing it to 8GB. I installed the PAE kernel to be able to access and use this new ram. The PAE kernel is working nearly flawlessly, EXCEPT that the reboot command does not work anymore. I cannot reboot my computer, I can only shut it down. Any time I try to reboot, whether it be from the menu or issuing the "sudo reboot" command, my computer hard locks and I have to force reset by cutting the power. I have checked and it does not seem that anyone else has this issue. What are my steps to try and solve this problem?

I initially thought it had something to do with ACPI issues in the kernel, but even if I boot with acpi=off, the issue still occurs.

---

### Post by amauk on 2011-07-01
/sbin/reboot is part of Upstart, so try reinstalling upstart```
sudo apt-get install --reinstall upstart
```

---

