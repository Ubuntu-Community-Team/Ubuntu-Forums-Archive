---
title: "Problem with nic Intel ether express 100 not coming up"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by jbpbis on 2007-08-23
Hello,

I just upgraded the Ubuntu on my Toshiba laptop (Satellite 5100-503) that has an Intel ethernet nic (according to lspci and the previous running version under Breezy) and since the upgrade to Edgy, the nic does not show up anymore.

Under Breezy, everything was fine. I had a 2.6.12 kernel and it was ok. Under Dapper, I had a 2.6.15 kernel and the nic never showed up, but I could still boot with the 2.6.12 kernel. I then upgraded to Edgy and a 2.6.17 kernel, and still the nic does not show up, but I cannot boot on the 2.6.12 kernel anymore (kernel panic).

lspci says that I have a Inter ethernet nic 82801CAM (ICH3) PRO/100 VE. I was using the e100 driver I guess on the Breezy version, and since I tried with the e100 or the eepro100 and nothing works. 

If I remove e100 from the modules and do a modprobe eepro100, I have a lot of stuff in dmesg with the MAC adress of the NIC, the IRQ (4), the rom selft test checksum passed ok, ... well, everything is fine, but ifconfig eth0 says '... device not found'. And nothing works to have ifconfig see 

Do you have any idea of the problem ? And maybe how I could revert using 2.6.12 working kernel/modules ?

Thank you.

---

### Post by jbpbis on 2007-08-23
OK, problem somehow solved. Shame on me : the nic was recognized as eth1 and not eth0. It took me so long to find this :(

---

