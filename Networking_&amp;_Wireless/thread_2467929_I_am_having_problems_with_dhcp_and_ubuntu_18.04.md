---
title: "I am having problems with dhcp and ubuntu 18.04"
date: 2021-10-13
forum: Networking &amp; Wireless
---

### Post by kgermann2 on 2021-10-13
I am trying to set a specific host name for each interface using dhcp on ubuntu 18.0.4.

I have the /etc/dhcp/dhclient.conf setup like this:
interface "eth0" {
  supersede host-name "vm1"
  send dhcp-client-identifier "vm1";
  send hostname "vm1";
}
interface "eth1" {
  supersede host-name "vm1s"
  send dhcp-client-identifier "vm1s";
  send hostname "vm1s";
}


dns with dnsmasq isn't picking up the hostnames for each interface. 

Any ideas on what I need to change to fix this?

---

### Post by wildmanne39 on 2021-10-13
Moved to Networking and wireless sub-forum.

---

