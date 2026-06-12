---
title: "dhcpd.conf shared-network help"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by beckols on 2008-08-19
Ok, I have had a few posts here concerning this evolving matter.  I'm at the point where I almost have the whole setup figured out, but I am still having a problem.

Background:
2 Servers (each with dsl line, and connected to network)
The two servers have ip addresses of 10.1.1.1 and 10.1.1.2
This network consists of about 80-90 computers

In my dhcpd.conf I have a shared-network statement so that each lease that is given out will have a random gateway of either 10.1.1.1 or 10.1.1.2

Here is my dhcpd.conf

```

ddns-update-style none;



option domain-name-servers 4.2.2.2, 4.2.2.3;



default-lease-time 172800;

max-lease-time 1209600;



authoritative;



shared-network net12 {

subnet 10.1.1.0 netmask 255.255.255.0 {

	range 10.1.1.5 10.1.1.250;

	option subnet-mask 255.255.255.0;

	option broadcast-address 10.1.1.255;

	option routers 10.1.1.1;

	option domain-name-servers 4.2.2.2, 4.2.2.3;

}

subnet 10.1.2.0 netmask 255.255.255.0 {

	range 10.1.2.5 10.1.2.250;

	option subnet-mask 255.255.255.0;

	option broadcast-address 10.1.2.255;

	option routers 10.1.1.2;

	option domain-name-servers 4.2.2.2, 4.2.2.3;

}

}


```

According to the man page of dhcpd.conf: "If any subnet in a shared
network has addresses available for dynamic allocation, those addresses are collected into a common pool for that shared network and assigned to clients as needed.  There is no way to distinguish on  which  subnet of a shared network a client should boot."

My problem is that all of the leases in /var/lib/dhcp3/dhcpd.leases have ip addresses of 10.1.1.2**
This doesn't seem to be very random to me :)

Could anyone help me figure this out, it is pretty urgent.

Thank you!

---

