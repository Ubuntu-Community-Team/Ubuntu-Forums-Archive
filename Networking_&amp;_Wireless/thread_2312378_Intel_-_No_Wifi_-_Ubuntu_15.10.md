---
title: "Intel - No Wifi - Ubuntu 15.10"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by aj21 on 2016-02-04
Hello,

I'm new around here, and I can't seem to get my wifi working with dual-booted ubuntu. I have an edge 2-1580, fairly new.

When I run lspci I get this back: 

02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)

I think maybe there isn't a driver for my wifi card for ubuntu, but surely this can't be the case? If it is, perhaps there is a substitute? 

I can't stay wired forever!

Thanks,

AJ

---

### Post by chili555 on 2016-02-04
There is a driver and there is also firmware, but we need more details before we can propose a solution. Please run and post from the terminal:```
lspci -nnk | grep 0280 -A2
sudo modprobe iwlwifi && dmesg | grep iwl
```Thanks.

---

