---
title: "Radvd setup questions"
date: 2023-05-01
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2023-05-01
I am trying to set up my server (ubuntu server 22.04.2) as an ipv6 router (it's already working as an ipv4 router). Unfortunately, there is not much information around, but after some research I was able to fix problem with setting accept_ra=2.
Now for the next steps.
1. Getting prefix from Comcast. I'm too lazy to install wide-dhcp, so decided to do it the simplest way. And it worked:

dhclient -6 -v -P --address-prefix-len 64 eno1

where eno1 is my WAN interface.
I've got the prefix, I can see it in the dhclient6.leases file:

iaprefix 2601:444:300:ae3::/64

But it's a dynamic prefix, how do I set it up in radvd? I tried to set it to ::/64:

interface enp4s0
{
AdvSendAdvert on;
MinRtrAdvInterval 10;
MaxRtrAdvInterval 100;
prefix ::/64
{
AdvOnLink on;
AdvAutonomous on;
AdvRouterAddr off;
};
};

where enp4s0 is my LAN interface. It didn't work, because, obviously, I'm getting prefix for eno1, which is WAN interface.

When I changed prefix to the one received from Comcast:

interface enp4s0
{
AdvSendAdvert on;
MinRtrAdvInterval 10;
MaxRtrAdvInterval 100;
prefix 2601:444:300:ae3::/64
{
AdvOnLink on;
AdvAutonomous on;
AdvRouterAddr off;
};


};

Everything is working just fine. Now is the hard question: how do I set up radvd with dynamic prefix received by dhclient?

---

### Post by Alex_Filonov on 2023-05-06
OK, I found out that it's not radvd problem. Somehow prefix delegation is not working. I'm using dhclient from isc-dhcp-server package. There is a bug ([https://bugs.launchpad.net/netplan/+bug/1771886](https://bugs.launchpad.net/netplan/+bug/1771886)), PD is not working with netplan. I tried to use the workaround listed in the bug, set the following values in /etc/systemd/network/10-netplan-eno1.network.d/ipv6_pd_ra.conf:

[Network]
IPv6SendRA=yes
DHCPv6PrefixDelegation=yes
IPv6PrivacyExtensions=yes
IPv6AcceptRA=yes

Still no luck. Any suggestions?

---

### Post by Alex_Filonov on 2023-05-17
Closing this thread as solved. So far, combination of 

echo 2 > /proc/sys/net/ipv6/conf/eno1/accept_ra

and

dhclient -6 -v -P --address-prefix-len 64 eno1

is working.
I have other questions about ipv6 setup, opened another thread [here]("https://ubuntuforums.org/showthread.php?t=2486913")

---

