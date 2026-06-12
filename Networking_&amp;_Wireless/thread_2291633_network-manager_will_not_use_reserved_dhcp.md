---
title: "network-manager will not use reserved dhcp"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by rican-linux on 2015-08-21
On my windows dhcp server at the office I have set a reservation for my laptop. However when I restart dhcp network-manager is still getting the old ip address. When I looked at the traffic in wireshark I say that my laptop was requesting to the old ip address. I tried removing the */var/lib/dhcp/dhclient.leases* file and restarting dhcp. Still it would not work. I am running Kubuntu 14.04. Any help would be appreciated.

Thanks!

---

### Post by TheFu on 2015-08-21
DHCP reservations use MAC addresses. If the same network port is used, you will get the same IP. The OS doesn't matter.

Or did I misunderstand something?

---

### Post by rican-linux on 2015-08-21
Yes I set the reservation on my dhcp server to particular ip address. My machine was already on the network and had an address assigned. When I restarted dhcp I wanted to get the address I assigned to the server but instead it just renewed the address it already had.

---

### Post by TheFu on 2015-08-21
The client won't ask against until the lease time is up - unless you reboot.

---

### Post by weatherman2 on 2015-08-21
Try this, to release then renew your IP:

```

sudo dhclient -r
sudo dhclient

```

Double check that your MAC address is in fact correct in the router reservation, if you typed it manually.

---

### Post by rican-linux on 2015-08-22
I already tried that and have triple checked the reservation. Still gets the same ip and not the reserved one. I am wondering if it being cached somewhere else...

---

### Post by TheFu on 2015-08-22
> **rican-linux said:**
> I already tried that and have triple checked the reservation. Still gets the same ip and not the reserved one. I am wondering if it being cached somewhere else...

If there is more than 1 DHCP server on the network, which ever answers first is used.

---

### Post by rican-linux on 2015-08-22
that could be it, will double check.

---

