---
title: "No subnet declaration for vmnet8"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by anxean on 2007-05-18
Trying to get my dhcpd running at home heres what happens

No subnet declaration for vmnet8 (192.168.85.1).
Please write a subnet declaration in your dhcpd.conf file for the
network segment to which interface vmnet8 is attached.
exiting.

heres my conf

subnet 192.168.1.0 netmask 255.255.255.0
 {
	option netbios-name-servers 192.168.1.1;
	option domain-name-servers 192.168.1.1;
	option domain-name "microsoft";
	option broadcast-address 192.168.1.255;
	option routers 192.168.1.1;
	range 192.168.1.100 192.168.1.130;
	}

any ideas?

---

### Post by veloce on 2007-05-19
> **anxean said:**
> Trying to get my dhcpd running at home heres what happens

No subnet declaration for vmnet8 (192.168.85.1).
Please write a subnet declaration in your dhcpd.conf file for the
network segment to which interface vmnet8 is attached.
exiting.

heres my conf

subnet 192.168.1.0 netmask 255.255.255.0
 {
	option netbios-name-servers 192.168.1.1;
	option domain-name-servers 192.168.1.1;
	option domain-name "microsoft";
	option broadcast-address 192.168.1.255;
	option routers 192.168.1.1;
	range 192.168.1.100 192.168.1.130;
	}

any ideas?

What are you trying to achieve?  You obviously have vmware installed on this machine, vmware runs it's own dhcp server for host only and nat networks.  It's the nat one that's confusing dhcpd.

Are you using the nat network for your vms?  If not you could disable it. 

If this is the latest version, run:
vmware-config-network.pl

Earlier versions had the network in with other stuff and you run:

vmware-config.pl

---

### Post by anxean on 2007-05-19
i am trying to just randomly distribute an address for each windows machine my network,  I removed vmware only to return with the following:

No subnet declaration for eth1 (192.168.85.1).
Please write a subnet declaration in your dhcpd.conf file for the
network segment to which interface vmnet8 is attached.
exiting.


p.s. I am not using nat and I am aware of some netbios or wins option but not sure where to put them

---

### Post by veloce on 2007-05-19
> **anxean said:**
> i am trying to just randomly distribute an address for each windows machine my network,  I removed vmware only to return with the following:

No subnet declaration for eth1 (192.168.85.1).
Please write a subnet declaration in your dhcpd.conf file for the
network segment to which interface vmnet8 is attached.
exiting.


p.s. I am not using nat and I am aware of some netbios or wins option but not sure where to put them

By still mentioning vmnet8, it implies that vmware is still there in some form (I think).  Does vmnet8 show up in the output of ifconfig?

---

