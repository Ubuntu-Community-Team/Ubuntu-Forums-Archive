---
title: "acer aspire 5000 not a broadcom..."
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by notsteve on 2007-04-02
so i have an acer aspire 5000 now i in the proscess of installing my network card driver with ndiswrapper. but after i blacklist and type the code: sudo rmmod bcm43xx,  it claims that module does not exist.

can anyone help.

---

### Post by Floppyjoe on 2007-04-02
> **notsteve said:**
> so i have an acer aspire 5000 now i in the proscess of installing my network card driver with ndiswrapper. but after i blacklist and type the code: sudo rmmod bcm43xx,  it claims that module does not exist.

can anyone help.
This could happen if you rebooted your computer inbetween blacklisting the module and issuing the rmmod bcm43xx
Then move to the next step in the guide.

---

### Post by notsteve on 2007-04-03
when i tinued to the next step it claimed that it couldn copy bcmw15.inf at /usr/sbin/ndiswrapper-1.8 line 144

---

### Post by notsteve on 2007-04-03
ok so  countinued with the steps and after i wrote:
sudo modprobe ndiswrapper, it replied:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko):

---

