---
title: "normal dhcp client activity?"
date: 2018-05-15
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-05-15
I notice that every few minutes, my devices are checking in to the dhcp server.  The traffic looks like this (for *one *device):
dhcrequest @ 1050
dhcpack @ 1050
dhcrequest @ 1055
dhcpack @ 1055
dhcrequest @ 1059
dhcpack @ 1059

Is this normal?

---

### Post by ralen1225 on 2018-05-24
Whenever the address ages to half of the lease time, the address is reconfirmed by the client machine. You will get fewer of these messages if you raise the lease time. If you are using isc-dhcp the default location is /etc/dhcp/dhcpd.conf. The default lease time is probably near the top of the file. Mine is 5 minutes,  which I believe is the default. That causes each client to confirm it's lease every 2.5 minutes.

---

### Post by SeijiSensei on 2018-05-24
I use lease times of 2592000 seconds (thirty days). Unless you are supporting a network with more workstations than available addresses, there is no reason to use short lease times.

I believe my router defaults to 2^32-1 seconds, the largest integer representable in 32 bits.

---

