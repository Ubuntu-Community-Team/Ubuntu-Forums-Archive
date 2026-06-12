---
title: "Different Static IP's in Different locations for my laptop"
date: 2015-10-12
forum: Networking &amp; Wireless
---

### Post by mr-gary-waters on 2015-10-12
I am trying to have my laptop work in my 2 offices via static ip. 
I am running Ubuntu 14.04 and Gnome-Shell, but I cant seem to get this work like I thought it would.

I vaguely remember being able to assign different IP's to the same NIC in the network manager, as long as I named the nic different.
It would appear I can not do that anymore. I have 1 nic, and each time I save it, but I cant make a new nic or location.

Suggestions ?

Thanks,
WoodTablet

---

### Post by SeijiSensei on 2015-10-13
You can assign a second IP address from the command line with 
```
sudo ifconfig eth0:0 10.10.10.10 netmask 255.255.255.0
```
using the approrpriate address and netmask.  However routing will be wrong since the default gateway will still be assigned to the address in the subnet assigned to eth0.  You could write a little script to handle this as well:
```

#!/bin/bash
ifconfig eth0:0 10.10.10.10 netmask 255.255.255.0
ip route del default 
ip route add default via 10.10.10.1

```
replacing 10.10.10.10 with the IP address you want to assign to your computer and 10.10.10.1 with the IP address of the gateway on the work network.

Put those commands into /usr/local/sbin/switch_network and use "chmod +x /usr/local/sbin/switch_network" to make the file executable.  Now you should be able to run
```
sudo switch_network
```
at a prompt to use the secondary address.

---

### Post by mr-gary-waters on 2015-10-14
That naturally works, suggestions on how to add this to upstart so it happens automatically ?

I added an arpping to the bash script to check the mac address of the gateway so I wont get this address if I am not in the building.

Note: I currently have it in rc.local.

---

