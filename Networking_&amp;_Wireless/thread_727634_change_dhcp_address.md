---
title: "change dhcp address"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by anliveyak on 2008-03-18
i am trying to get a new ip address from a dhcp server, but it allways gives me the same one. i know how to subnet and statically change the address. i want to know if there is any way to reject the address it keeps giving me and force it to give me a different one. thanks

---

### Post by Eiríkr on 2008-03-18
Generally speaking, DHCP servers grant address leases within a range, and will usually pick the first available address within that range for the next lease.  So presumably the only way to force a different DHCP address, short of reconfiguring the available range in the DHCP server config files, is to have some other machine on the network be the first to grab the address you don't want.  

Cheers,

Eiríkr

---

### Post by anliveyak on 2008-03-18
thanks for your reply. I know what a DHCP server is and how it runs, i have a CCNA degree. i just wish there was an easier and faster way to do it. maybe i will just install another network card and write some shell script...

---

### Post by Eiríkr on 2008-03-18
Glad to hear it, and no offense meant.  I seldom know who I'm replying to, and have learned over time that it's generally better to err on the side of too much information rather than not enough.  :)

One other option that some DHCP servers offer is the ability to assign specific IP addresses to certain clients by MAC address.  Perhaps that would fit your bill?

Cheers,

Eiríkr

---

### Post by anliveyak on 2008-03-19
its ok, i know what you mean with not knowing people's knoledge. i think i can just get the job done by switching which card i am using and have 2 ip's at the same time.

---

### Post by peterquistgard on 2008-04-30
Hi guys. I'm looking for way to isolate my ip address from eth0 (my NIC) and assign an alias to it. I'm planning to use it in a proxy autoconfiguration script. I wrote this short script:

IP=`ip route show | grep src | awk '{print $NF}'`
sudo sed -i "/eth0Address/c\\$IP eth0Address" hosts

This script works fine :guitar:. It updates the ip address for the alias "eth0Address". 

**Does anyone know how I can get this script to run every time i get a fresh ip address using DHCP??** :confused:

Thanks in advance.

---

