---
title: "Network Interface Ordering"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by snacker on 2008-03-08
I have 2 "physical" network connections: ath0 (ip=192.168.0.1) and eth0.(ip=192.100.1.1)

ath0 is a wireless connection to a netgear router which I can use to access other computers and the internet.

eth0 is an ethernet (hardwire) connection.  It is a private network which I have to use to connect to special hardware which runs embedded linux.  It does not have access to the internet.

So my problem is I want to use the wireless connection (ath0) to access the internet and other computers on the network while I'm also connected to eth0 to only access that special hardware.

I've used "Network Manager" to setup the DNS to use the wireless router.
I've checked and rewritten /etc/resolv.conf to make sure it is using 192.168.0.1.

If I have them both connected it hangs trying to resolve a domain name.
It seems to me that it is using eth0 (192.100.1.1) trying to contact a DNS at (192.168.0.1) instead of using ath0 to connect to 192.168.0.1 (the address of ath0).

**So how can I specify that all DNS lookups should be done through ath0 instead of eth0???**

---

### Post by Eiríkr on 2008-03-10
What does your /etc/network/interfaces file look like?

Cheers,

Eiríkr

---

### Post by snacker on 2008-06-17
I've figured out a workaround via manipulating the routing tables to send traffic to one or the other interface based on ip address.

I'm sending all addresses like 192.100.*.* to eth0 (wired) and all the others to ath0 (wireless).

The commands I'm using to setup the routing tables are:

```
sudo route add -net 192.100.0.0 netmask 255.255.0.0 dev eth0
sudo route del -net 0.0.0.0 dev eth0

```

NOTE that I had to **del**ete the 0.0.0.0 address, otherwise the OS was still trying to send all traffic to eth0.  Even though there was an entry for 0.0.0.0 for ath0 (wireless) nothing would respond... so had to delete 0.0.0.0 for eth0 (wired).

---

