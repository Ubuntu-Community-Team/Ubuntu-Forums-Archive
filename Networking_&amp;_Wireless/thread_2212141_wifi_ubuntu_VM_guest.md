---
title: "wifi ubuntu VM guest"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by mrinal2 on 2014-03-19
i have installed guest ubuntu virtual in oracle vm box,i'm not getting any result for this #apt-get update/upgrade command
it says (101: network is unreachable) and (could not resolve us.archive.ubuntu.com)....give me any solution

---

### Post by varunendra on 2014-03-21
Welcome to Ubuntu Forums Mrinal!

The guest OS (the one inside the VM) usually gets its Internet connection from the Host. Is the host connected to Internet?

While creating the VM, which kind of networking did you select in the VM? NAT, Bridged, Host only....?

Please provide as much details as you can about the network setup of the VM and how it is supposed to get Internet connection.

---

