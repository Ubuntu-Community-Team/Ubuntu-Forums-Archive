---
title: "ipw2200 switches between eth1 and eth2"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by notiones on 2006-08-24
I recently installed an ipw2200 card in a Gateway MX3225 for a client. I booted up, configured the card and all was good. I didn't install any firmware or anything because it is already there. It just worked. The problem I am having is that sometimes when I start the laptop the ipw2200 comes up as eth1 and sometimes it comes up as eth2. The closest thing I have seen to any error messages is this.

Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!

I don't think it s related though. If I had to hazard a guess it would be that sometimes it shows up early in the boot sequence and then shuts down and thus gets relegated to eth2.

---

### Post by notiones on 2006-08-25
This is not going to be an issue since I set up /etc/interfaces with both eth1 and eth2 configured. 

I would like to know for future reference if anyone has fixed this problem.

Thanks,

Steve

---

