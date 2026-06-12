---
title: "NetPlan - Bridge Over Bonded NICs"
date: 2021-03-08
forum: Networking &amp; Wireless
---

### Post by Alan5127 on 2021-03-08
Hi All,

I am setting up Ubuntu Server 20.04.2 LTS as a KVM Host.

When installing Ubuntu Server, I chose to bond the two NICs on the (physical) server, as it seemed to make sense.

I now need to setup a Bridge for the Guest OSs to be able to work on my LAN.

I found this article describing how to do it (albeit based on Ubuntu Server 18.04 LTS):

[https://www.aptgetlife.co.uk/setting-up-a-bond-and-bridge-in-netplan-on-ubuntu-18-04/](https://www.aptgetlife.co.uk/setting-up-a-bond-and-bridge-in-netplan-on-ubuntu-18-04/)


This is my current /etc/netplan/00-installer-config.yaml:

```
# This is the network config written by 'subiquity'
network:
  bonds:
    bond0:
      addresses:
      - 172.25.25.3/24
      gateway4: 172.25.25.254
      interfaces:
      - eno1
      - eno2
      nameservers:
        addresses:
        - 172.25.25.254
        - 192.168.1.254
        - 8.8.8.8
        - 9.9.9.9
        search: []
      parameters:
        mode: balance-rr
  ethernets:
    eno1: {}
    eno2: {}
  version: 2


```

This is what I have drafted based on the article above:

```
# This is the network config written by 'subiquity'
network:
  bridges:
    br0:
      addresses:
      - 172.25.25.3/24
      dhcp4: false
      gateway4: 172.25.25.254
      nameservers:
        addresses:
        - 172.25.25.254
        - 192.168.1.254
        - 8.8.8.8
        - 9.9.9.9
        search: []
      interfaces:
        - bond0
  bonds:
    bond0:
      interfaces:
      - eno1
      - eno2
      parameters:
        mode: balance-rr
  ethernets:
    eno1:
      addresses: []
      dhcp4: false
      dhcp6: false
    eno2:
      addresses: []
      dhcp4: false
      dhcp6: false
  Version: 2
```

Question 1) In the sample, they have used an 'address' of '192.168.10.30'.  My current config includes the subnet, and is '172.25.25.3/24'.  How does their example know what the subnet is?  Is it implied in the gateway, and not required to be explicitly stated?  Is there any harm in stating it explicitly the way I have my current config?

Question 2)  The example explicitly sets DHCP to FALSE.  Is that required, or can I just use the curly brackets I have currently?  If not, what is the actual difference? 

Question 3)  Is there anything else in the proposed config that looks wrong or raises any questions?


Thanks,

Alan.

---

