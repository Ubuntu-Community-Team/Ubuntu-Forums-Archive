---
title: "System obtains two IP addresses from DHCP"
date: 2021-12-02
forum: Networking &amp; Wireless
---

### Post by totti4ever on 2021-12-02
Hey, I was wondering how this could be:
My router says it assigned two different IPs to my home server and I can use both to ping and ssh onto it. They do have the same MAC address but different DHCP client ids.

Looking at *ifconfig* eno2 only one address is shown, looking at */var/lib/dhcp/dhclient.leases* only the other one is shown. I thought my networking master was netplan, having quite a simple setup:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno2:
      dhcp4: yes
```

What could I have done wrong or which configs could live on from old sates of the system bringing up this odd behaviour?

P.S.: I'm pretty sure this is also the reason my bonding wasn't working

---

### Post by Doug S on 2021-12-02
Which version of Ubuntu?

I wonder if somehow you have got a mixture of systemd-networkd and the old way going on at the same time. I am not an expert, and actually avoid using netplan entirely, preferring systemd-netorkd directly. You appear to have dhclient running, which I don't think it should be. There shouldn't be a dhclient.leases file. I think you have to decide one way or the other between systemd-networkd (which netplan is merley a front end for) or ifup/down (or whatever the official name for the old way is).

---

### Post by damian7820 on 2021-12-02
It could be the your computer has an outdated ARP table, witch causes the crash. You can list the ARP table with $ arp -a and review the result for compared with your correct network interface.

---

### Post by TheFu on 2021-12-03
Any server should have a static IP assigned and not trust DHCP.  This is important for a number of reasons, including security and firewall rules.  There are attacks against DHCP servers that can do some nasty things. Why risk it?  Just setup static IPs for every device that isn't portable.  Some IoT devices should use DHCP reservations to get the same IP assigned always, but only devices from outside your home - like when guests come for a visit - should truly have random DHCP  addresses.

---

