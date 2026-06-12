---
title: "IPtables &amp; 2 gateways"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by john328 on 2014-12-03
Dear all,
   
  I’ve got 2 DHCP servers / ubuntu 14.04.they are configured in failover mode (primary/secondary).
   
  They work very well but I have the following issue:
   
  The primary has got 2 NW-cards, eth0 for assigning the IP-Addresses (172.20.32.11 – NW: 172.20.32.0) and the other one – eth1- is for accessing the internet (it’s actual a Vlan -10.0.19.11 with 10.0.19.5 as gateway ). 
   
  The secondary has got also 2 NW-cards, eth0 for assigning the IP-Addresses (172.20.32.12 – NW: 172.20.32.0) and the other one – eth1-is for accessing the internet (it’s the same Vlan but with the IP address-10.0.19.12 and 10.0.19.5 as gateway ). 
   
  The issue is, if I switch of the primary (for testing) clients loose the connectivity for couple of minutes until they get the new gateway (from the secondary 10.0.19.12) and then it works again (the same happiness if I turn on the primary).
   
  Is there any way to point both servers to the same gateway ?, which is the gateway of of the Vlan (10.0.19.5) and not just to the second network card in both servers, e.g by editing the IPtable

   
  Configuration of eth1 (vlan) for primary server is:
  address  10.0.19.11
              netmask 255.255.255.0
              gateway 10.0.19.5
   
  Configuration of eth1 (vlan) for secondary server  is:
  address  10.0.19.12
              netmask 255.255.255.0
              gateway 10.0.19.5
   
  and my Iptable looks as follows:
   
     iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

   
              iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
   
              iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

   
  I would appreciate any help or advice.

   
  May thanks

---

### Post by Doug S on 2014-12-03
Hi and welcome to Ubuntu forums,

I am having difficulty understanding the correlation between the description of your network and your iptables. From your description, would NOT have expected this:```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```But would have expected something like this:```
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```It isn't really relevant, but I prefer to use SNAT (primary):```
iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 10.0.19.11
iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```Edit: I assume your default policy for FORWARD is DROP

---

### Post by john328 on 2014-12-08
Many thanks Doug S,

That's very kind of you but didn't solve my problem with the 2 gateways.

Hope someone will be able to help.

Thanks again

John

---

