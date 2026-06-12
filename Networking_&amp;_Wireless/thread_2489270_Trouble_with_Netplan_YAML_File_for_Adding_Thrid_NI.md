---
title: "Trouble with Netplan YAML File for Adding Thrid NIC"
date: 2023-07-24
forum: Networking &amp; Wireless
---

### Post by glued-2-keyboard on 2023-07-24
Ubuntu 20.04.6 LTS System with three NIC cards.  

NIC 2 (a,b) & 3 are in bridge mode.

When NIC 3 was setup as a bridge on subnet 192.168.5.0 everything was working fine BUT when I attempted to change NIC 3 and set it up as a bridge on subnet 192.168.1.0 the ONBOARD NIC is unreachable from the LAN (192.168.1.0) .

Not sure what I am doing wrong and would appreciate some assistance.

1. Onboard NIC
    aa:aa:aa:aa:aa:aa    192.168.2.2 <-- STOPS WORKING when SINGLE NIC bridge is set to 192.168.1.25

2. Dual NIC
   (Port A )   bb:bb:bb:bb:bb:bb    192.168.3.2 
   (Port B )   cc:cc:cc:cc:cc:cc    192.168.4.2 

3. Single NIC
    dd:dd:dd:dd:dd:dd     192.168.1.25  <--- DOES NOT WORK
dd:dd:dd:dd:dd:dd     192.168.5.2  <--- WORKS


onboard-NIC.yaml

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eth1:
      match:
        macaddress: aa:aa:aa:aa:aa:aa
      addresses: [192.168.2.2/24]
      gateway4: 192.168.2.1
      nameservers:
        addresses: [192.168.2.1]
        search: [localdomain]

```

singleNIC.yaml

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eth4:
      match:
        macaddress: dd:dd:dd:dd:dd:dd

  bridges:
    br2:
      interfaces: [eth4]
      addresses: [192.168.5.2/24]    #If I switch this to 192.168.1.25 then the onboard NIC 192.168.2.2 is unreacable from the LAN
      mtu: 1500
      nameservers:
        addresses: [192.168.5.1]
        search: [localdomain]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no

```

dualnic-port-1.yaml

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eth2:
      dhcp4: no
      match:
        macaddress: bb:bb:bb:bb:bb:bb
  
  bridges:
    br0:
      interfaces: [eth2]
      addresses: [192.168.3.2/24]
      mtu: 1500
      nameservers:
        addresses: [192.168.3.1]
        search: [localdomain]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no

```


dualnic-port-2.yaml

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eth3:
      match: 
        macaddress:  cc:cc:cc:cc:cc:cc
       
  bridges:
    br1:
      interfaces: [eth3]
      addresses: [192.168.4.2/24]
      mtu: 1500
      nameservers:
        addresses: [192.168.4.1]
        search: [localdomain]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no


```

---

