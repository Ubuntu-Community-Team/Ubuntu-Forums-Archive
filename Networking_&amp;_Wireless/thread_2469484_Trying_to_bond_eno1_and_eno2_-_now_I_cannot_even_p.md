---
title: "Trying to bond eno1 and eno2 - now I cannot even ping (18.04)"
date: 2021-11-30
forum: Networking &amp; Wireless
---

### Post by totti4ever on 2021-11-30
Bonding partner is a MikroTik Switch on SwitchOS, which also shows the bonding. The MikroTik Router on RouterOS shows four different DHCP leases, where I cannot ping a single of them, not talking about SSHing. Did I do something wrong on the Ubuntu side?





```
$ /etc/netplan$ sudo netplan --debug apply

** (generate:20924): DEBUG: 11:12:09.975: Processing input file /etc/netplan/01-malte.yaml..

** (generate:20924): DEBUG: 11:12:09.976: starting new processing pass
** (generate:20924): DEBUG: 11:12:09.976: Processing input file /etc/netplan/02-bonds.yaml..
** (generate:20924): DEBUG: 11:12:09.976: starting new processing pass
** (generate:20924): DEBUG: 11:12:09.976: We have some netdefs, pass them through a final round of validation
** (generate:20924): DEBUG: 11:12:09.976: bond0: setting default backend to 1
** (generate:20924): DEBUG: 11:12:09.976: Configuration is valid
** (generate:20924): DEBUG: 11:12:09.976: eno1: setting default backend to 1
** (generate:20924): DEBUG: 11:12:09.976: Configuration is valid
** (generate:20924): DEBUG: 11:12:09.976: eno2: setting default backend to 1
** (generate:20924): DEBUG: 11:12:09.976: Configuration is valid
** (generate:20924): DEBUG: 11:12:09.976: Generating output files..
** (generate:20924): DEBUG: 11:12:09.976: NetworkManager: definition eno1 is not for us (backend 1)
** (generate:20924): DEBUG: 11:12:09.977: NetworkManager: definition eno2 is not for us (backend 1)
** (generate:20924): DEBUG: 11:12:09.977: NetworkManager: definition bond0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:eno1 not found in {}
DEBUG:eno2 not found in {'eno1': {'dhcp4': True}}
DEBUG:bond0 not found in {}
DEBUG:Merged config:
network:
  bonds:
    bond0:
      dhcp4: true
      interfaces:
      - eno1
      - eno2
      optional: true
      parameters:
        mode: 802.3ad
  bridges: {}
  ethernets:
    eno1:
      dhcp4: true
    eno2:
      dhcp4: true
  vlans: {}
  wifis: {}


DEBUG:Skipping non-physical interface: lo
DEBUG:Skipping composite member eno1
DEBUG:Skipping composite member eno2
DEBUG:Skipping non-physical interface: docker0
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for eno1
DEBUG:netplan triggering .link rules for eno2
DEBUG:netplan triggering .link rules for docker0



```

---

### Post by Tadaen_Sylvermane on 2021-11-30
[https://netplan.io/examples/](https://netplan.io/examples/)
[https://www.snel.com/support/how-to-set-up-lacp-bonding-on-ubuntu-18-04-with-netplan/](https://www.snel.com/support/how-to-set-up-lacp-bonding-on-ubuntu-18-04-with-netplan/)

This is how I would write it.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  eno1:
   dhcp4: false
   dhcp6: false
  eno2:
   dhcp4: false
   dhcp6: false
 bonds:
  bond0:
   interfaces: [eno1, eno2]
   dhcp4: true
   optional: true
   parameters:
    mode: 802.3ad
```

I will readily admit I don't know yaml but I'm thinking it may be ordering. You need to define in order. The samples on the link above don't show putting the ethernets in the file but I've done that over time out of habit. Also the syntax on my interfaces line. I know it doesn't match the link but I must have been doing something wrong because the sample in the link never worked for me. Stumbled on this method some time after messing with it. Another habit. Don't add empty config lines. Just muddies up the config file.

---

### Post by totti4ever on 2021-12-02
okay, I put everything together and adapted it to your hints. netplan yaml now looks like this:
```
network:
    version: 2
    renderer: networkd

    ethernets:

      eno1:
        addresses: []
        dhcp4: false
        dhcp6: false
        optional: true
      eno2:
        addresses: []
        dhcp4: false
        dhcp6: false
        optional: true

    bonds:
        bond0:
            interfaces: [eno1, eno2]
            parameters:
                mode: 802.3ad
                transmit-hash-policy: layer3+4
                mii-monitor-interval: 1
                lacp-rate: fast
            dhcp4: true
            dhcp6: false
            optional: true
```


Still I have one big problem, which also occurs without the bond (don't think it happended before I played around though):
My router has 2 DHCP leases to the hostname of my homeserver, one with the MAC of eno2, which is fine and one with a MAC I cannot find when showing *ifconfig*. Odd thing is that I can ping that address and also ssh onto the server using both IPs.

I guess this weird problem might also continue to exist in the bonding world as both enos get an own IP assigned after a couple of seconds - and from then on the bond isn't working anymore while it worked perfectly for these few seconds.


My current setup for the basic setup without bonding with the off behaviour as described previously looks like this:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: yes
    eno2:
      dhcp4: yes
```

Could the old /etc/network/interfaces file have got something to do with it? I stripped it down to this as it had eno1 set to static from old days before:
```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback
```
*nothing in interfaces.d*

---

