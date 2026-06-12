---
title: "[SOLVED] eth0 and eth1 are confused"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by pappo on 2007-03-07
I have a second pc that is changing eth0 to eth1 after if finishes booting.
When I check the startup using dmesg, it shows the system detecting eth0
Here is the line from dmesg:

e100: Intel(R) PRO/100 Network Driver
e100: eth0: 3100_probe: addr:0xe9800000 irq:10 MAC addr 00:02:B3:2E:C7:7C

Then further down the dmesg listing is shows:

ADDRCONF (NETDEV_UP): eth1: link is not ready

When the maching completes booting and I login, I got to KMENU-->System Settings-->Network Settings, it only show eth1
When I do "sudo ifconfig" it only shows eth1 and lo

Any ideas about what is happening to my eth0 device ??

Thanks

---

### Post by netztier on 2007-03-07
> **pappo said:**
> I have a second pc that is changing eth0 to eth1 after if finishes booting.

Check the file **/etc/iftab** and see if there is a stale entry that matches some MAC address to eth0.

Either remove that entry or correct it so that it assigns the MAC address of your NIC to eth0.

best regards

Marc

---

### Post by pappo on 2007-03-07
netztierf,

Thank you.
You nailed that one.
deleting the entry in /etc/iftab fixed it.
I used to have a different card in that pc, and the iftab still had that old mac address in it.

When should I expect to see the iftab file show my new eth0 MAC address ?

I assigned 192.168.0.110 to that PC, and 192.168.0.111 to the other PC but I still cannot ping them.
I guess I better verify my crossover cable before I go any further.

Regards,
pappo

---

