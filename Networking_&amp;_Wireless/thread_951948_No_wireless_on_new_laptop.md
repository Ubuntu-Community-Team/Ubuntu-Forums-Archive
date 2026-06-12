---
title: "No wireless on new laptop"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by seattle vic on 2008-10-18
I just bought a very nice 17" Asus M70vm-c1 (from egghead, incredible deal).

So, not wanting to put up with vista, I've loaded both Hardy and Intrepid, but neither of them see my (or others in the neighborhood) wireless network.  I know the wireless components work, as vista sees it OK and I have another laptop working.

I presume it's intel hardware, as the mobo chipset is intel.  I haven't had to dive into wireless issues much, so could use some pointers, thanks.

I've done a lspci, and did not see a reference to wireless, however for ethernet controller it said:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 02)

also:

Network controller: Intel Corporatioin Unknown device 4232

---

### Post by mikewhatever on 2008-10-19
Can you post the outputs of <lspci> and <sudo lshw -C network>.

---

