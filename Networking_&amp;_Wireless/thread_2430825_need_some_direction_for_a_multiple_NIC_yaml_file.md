---
title: "need some direction for a multiple NIC yaml file"
date: 2019-11-08
forum: Networking &amp; Wireless
---

### Post by Heeter on 2019-11-08
Hi all,

So I can't figure out how to setup a yaml netplan file for 4 NIC cards.

The NIC IDs are eno1, eno2, eno3, eno4 all located in the same machine

Would like to use 192.168.1.11 for eno1, 192.168.1.12 for eno2, 192.168.1.13 for eno3, and finally 192.168.1.14 for eno4 all using a gateway and DNS of 192.168.1.1

If someone can help me with this, because I can't even ssh into this machine anymore. The more I try, the more I butcher the file.

Regards

---

### Post by johnarnold on 2019-11-08
The problem is you are trying to use 4 different NIC's all on the same subnet. There is no benefit to doing this and you'll end up with a very confusing network configuration.

---

### Post by Heeter on 2019-11-08
Well I have tried to run the vm's through one nic card and the netplan is angry and refused to work,

At least I got the vm's to function using pass through 

Maybe I can get some guidance on getting this yaml setup properly to only use one nic for my 3 vm's

God knows that googling this is even worse than the headache I already have

---

### Post by johnarnold on 2019-11-08
There is a good guide at [https://vitux.com/how-to-configure-networking-with-netplan-on-ubuntu/](https://vitux.com/how-to-configure-networking-with-netplan-on-ubuntu/)
If you are using DHCP then just make sure you leave out all the addresses/gateway info.

---

