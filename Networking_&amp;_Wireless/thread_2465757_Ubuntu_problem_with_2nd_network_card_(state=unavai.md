---
title: "Ubuntu problem with 2nd network card (state=unavailable)"
date: 2021-08-10
forum: Networking &amp; Wireless
---

### Post by antonis335 on 2021-08-10
[FONT=verdana]At work we have a Fujitsu 2530 M5 server running Ubuntu 20.04 (with GNOME) and for some reason while it sees the 2nd network card (Intel X722 with 4 ethernet ports), none of the ports come online when connected to Ethernet cables. The first network card works normally.

From the [FONT=var(--ff-mono)]journalctl network manager logs: 

[/FONT]state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
[FONT=var(--ff-mono)]
[/FONT]I tried different cables with the same result, i.e the ethernet LEDs do not even blink. However when using ethtool -p, the ethernet port LEDs blink normally. 
[/FONT]
[FONT=verdana]The ports in question are eno3 until eno6:
[/FONT]
$ sudo lshw -class network -short

H/W path         Device           Class          Description
============================================================
/0/2/0/3/0       eno3             network        Ethernet Connection X722 for 1G
/0/2/0/3/0.1     eno4             network        Ethernet Connection X722 for 1G
/0/2/0/3/0.2     eno5             network        Ethernet Connection X722 for 1G
/0/2/0/3/0.3     eno6             network        Ethernet Connection X722 for 1G
/0/0/0           enp179s0f0       network        I350 Gigabit Network Connection
/0/0/0.1         enp179s0f1       network        I350 Gigabit Network Connection
[FONT=verdana]
I am using Network Manager (file /etc/netplan/01-network-manager-all.yaml) and I've setup ports eno3 to eno6 to work with DHCP (for testing purposes), while the rest of the ports are static. I've confirmed that there is no configuration inside /etc/network/interfaces.
 [/FONT]
[FONT=verdana]Example DHCP config for interface eno3:
[/FONT]
network:
 version: 2
  renderer: NetworkManager
  ethernets:
 eno3:
  dhcp4: yes
  addresses: []

[FONT=verdana]I've made sure /etc/network/interfaces does not contain any network interface config.[/FONT]
[FONT=verdana]Nmcli shows the interfaces as unavailable:
[/FONT]
$ nmcli device status

DEVICE           TYPE      STATE        CONNECTION         
enp179s0f0       ethernet  connected    netplan-enp179s0f0 
enp179s0f1       ethernet  connected    enp179s0f1         
enx00243218010e  ethernet  connected    enx00243218010e    
eno3             ethernet  unavailable  --                 
eno4             ethernet  unavailable  --                 
eno5             ethernet  unavailable  --                 
eno6             ethernet  unavailable  --                 
lo               loopback  unmanaged    --
  
[FONT=verdana]I've tried ifdown then ifup/ restating networking, restarting network manager but nothing works. Any suggestions?[/FONT]

---

### Post by TheFu on 2021-08-12
20.04 doesn't use ifupdown.  It uses netplan.
network-manager gets confused by non-trivial setups. Use netplan with a better "renderer"

You'll need to setup static IPs for a server anyways, so just do that now.
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno3:
      dhcp4: true
      dhcp6: false
    eno4:
      dhcp4: true
      dhcp6: false
    eno5:
      dhcp4: true
      dhcp6: false
    eno6:
      dhcp4: true
      dhcp6: false

```
You can start with that, but using each will be difficult, since they will need a VIP for failover or bonding to share the total possible bandwidth (1 Gbps per stream limit) or if they are on different subnets, you'll need to manually setup specific routes for each.

When posting commands, output and config files here, it is mandatory that code tags be used, as I've done.  Otherwise indentation is lost and since YAML cares about indentation, we can't tell if the file is correct without it.

---

