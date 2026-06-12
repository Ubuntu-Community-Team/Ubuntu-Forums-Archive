---
title: "Replacing NIC breaks network"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by chris1103 on 2006-11-10
I have a Ubuntu 6.06 server (no GUI) with an Intel 10/100 Ethernet NIC (e100 driver).  I was testing whether I could replace a faulty NIC without reconfiguration, so I replaced the NIC with another identical (known good) Intel 10/100 NIC, and now the system cannot find eth0 at bootup.  lsmod shows that the e100 module is installed.  When I manually run "ifup eth0" it gives me an error saying the interface eth0 cannot be found.  I tried another Intel 10/100 NIC with identical results.

I reinstalled the original NIC and eth0 comes right up at boot, no problems.

This ought to be simple enough to do, can anyone help?

Thanks,

Chris

---

### Post by FrodoB on 2006-11-10
Have you checked dmesg to see what the new card is being discovered as? Maybe it is being assigned to a different name.  How about the output from ifconfig as well.

---

### Post by cylon359 on 2006-11-10
Does /etc/iftab contain the MAC address of the old card?  If so, put the new MAC address there.

---

### Post by chris1103 on 2006-11-10
OK, that fixed it!

I changed the MAC address in /etc/iftab to the MAC address of the replacement NIC, shutdown the server, replaced the NIC, rebooted, and the network came right up with no problems.

I was used to SuSE, and the networking in Ubuntu is quite a bit different than other Linux distros I've used.

Thanks very much!

Chris

---

### Post by FrodoB on 2006-11-10
Good catch cylon359.

---

