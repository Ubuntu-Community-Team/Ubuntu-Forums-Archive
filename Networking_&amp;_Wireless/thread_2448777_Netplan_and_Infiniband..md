---
title: "Netplan and Infiniband."
date: 2020-08-13
forum: Networking &amp; Wireless
---

### Post by falloutboy2 on 2020-08-13
O.K, Time marches forward and changes are made to whit I have a question, regarding Netplan, I note that they have the following ID's:
ethernets,
modems,
wifis,
bridges,
bonds,
tunnels,
vlans.

Now I have two Ethernet connections and they look like they shouldn't be to hard to setup - but there is nothing in the ID sections that refer to Infiniband which is in itself not a match for any of the ID types, my first though was an ID of ethernet but it just does not sit quite right, my board is a Mellanox and from how I have configured in the past I know that operating as user root ( I.E after a sudo -s ) I perform the following:

/etc/init.d/openibd restart
mst start <- this actually initializes the drivers.
( at this point the ip address can be configured. )

I am not sure how to shoehorn this into netplan, can anyone provide some guidance please.

---

