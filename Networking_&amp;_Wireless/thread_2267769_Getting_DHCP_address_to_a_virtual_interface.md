---
title: "Getting DHCP address to a virtual interface"
date: 2015-03-03
forum: Networking &amp; Wireless
---

### Post by UbPM on 2015-03-03
I am trying to create virtual interfaces and get dhcp addresses, but it does not work. Appreciate if anyone can let me know what am I doing wrong

I create virtual interface using the following
> sudo ip link add type veth 

When I do that it creates 2 virtual interfaces - veth0 and veth1. I am able to see it using "ifconfig veth0" and "ifconfig veth1"

I want to assign dynamic ip address to veth0 and veth1 using dhcp. I am not sure how to do it.

I have tried to do the following but it does not work
> sudo ifconfig veth0 inet dhcp start

or 
> sudo ifconfig veth0 dhcp start


I get the error "dhcp: Unknown host"

My suspicion is it is taking dhcp as a host name and looking for it.

I am not sure what is the right way to do this. I really appreciate any suggestions.

dhcpclient is running and I have verified using "ps -ef" command.

I am using Ubuntu 14.04

---

