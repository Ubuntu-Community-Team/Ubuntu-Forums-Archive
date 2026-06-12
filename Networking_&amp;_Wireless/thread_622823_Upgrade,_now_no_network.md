---
title: "Upgrade, now no network"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by Andrew Doades on 2007-11-25
Hi, I am running Ubutnu server in VMware server 1.0.4, I upgraded from 7.04 to 7.10 last night, sadly the virtual machine shutdown last night and when I booted back up, I have no network, Ubuntu can detect my network, I really need my Virtual machine, and network, I also can install some packages to try and install other stuff becuase I have no internet, Bloody thing.

All help very Appreciated.

Cheers, Andrew

---

### Post by kevdog on 2007-11-25
During the upgrade a new kernel was installed, hence any custom kernel modules you inserted into the previous kernel (ie ndiswrapper, madwifi, or others) are not included in the new kernel.  You will need to reinsert these modules into the new kernel.  B/c you didn't give any details about the drivers you were using before I can't help you much.  Since you upgraded, the old kernel should still be on your system.  When your system boots you will need to enter the grub menu from where you can choose what kernel version you want to boot.  Boot into the old kernel, download what ever you need to, and then reboot into the newer kernel and install the packages.

---

### Post by Andrew Doades on 2007-11-25
Cheers, I will do that now and get back to you!!

Cheers,
Andrew

---

### Post by Andrew Doades on 2007-11-25
All seems to have worked got installed what I needed, and got my interbet back!

Cheers, Loads!!!!
Andrew

---

