---
title: "unable to detect wifi after updating"
date: 2018-07-04
forum: Networking &amp; Wireless
---

### Post by kate552 on 2018-07-04
hey guys , m using ubuntu 16.4 since 2 months, i recently updated, but after update system is unable to detect any wifi. kindly help

---

### Post by lotharmat on 2018-07-04
Do you have the Broadcom wifi chipset?

The 4.15 kernel is lacking the correct firmware I believe.

What happens when you boot into 4.13 Kernel?

---

### Post by simon114 on 2018-07-04
I reverted to 4.13 by pressing shift on boot, (actually had to esc on purple screen and then shift to get to advanced options

then chose boot 4.13 generic

But then had to uninstall and reinstall wireless drivers as follows

```

sudo apt-get purge bcmwl-kernel-source
sudo apt update
sudo apt-get install bcmwl-kernel-source

```

Hope That helps

I just want to set 4.13 as default now, Time to research again..

---

