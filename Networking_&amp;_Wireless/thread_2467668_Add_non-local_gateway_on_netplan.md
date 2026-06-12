---
title: "Add non-local gateway on netplan"
date: 2021-10-03
forum: Networking &amp; Wireless
---

### Post by Tacioandrade on 2021-10-03
I have a VM running on OVH where they give me an IP in one range and a gateway in another! For example the IP given by OVH is 200.0.0.2/32 and the gateway is 191.0.0.254.


After much suffering I managed to put the network manually by running the following commands in the terminal:


route add 191.0.0.254/32 ens18
route add default gw 191.0.0.254


But the problem is that every reboot to apply kernel patch I have to access the Proxmox interface, open the shell and run the commands again.


I would like to know how I can put non-local gateways in netplan.


Thank you in advance for your help.

---

### Post by TheFu on 2021-10-04
netplan yaml supports that. netplan.io has details.

---

