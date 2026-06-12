---
title: "Netplan with Bond and Bridge setup on 18.04"
date: 2019-01-18
forum: Networking &amp; Wireless
---

### Post by bassman5066 on 2019-01-18
I currently have a KVM host running 18.04 server. The bridge (br0) is currently pointing at one physical NIC (enp1s0f0) but the system has two so I would like to bond them together and point the bridge to use the bonded interface instead. I have done this in the past with 16.04 (albeit without the bridge) and was able to get bonding working but am having trouble with the new netplan syntax. 

Here is what I want: 

A static IP for the server of 10.1.10.10, GW of 10.1.10.1, and DNS servers of 8.8.8.8,8.8.4.4
bond0 to consist of enp1s0f0 and enp1s0f1 in balance round robin mode
br0 to consist of bond0 

```

[FONT=courier new]# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd

  ethernets:
    enp1s0f0:
      dhcp4: no
    enp1s0f1
      dhcp4: no

   bonds:
    bond0: 
      dhcp4: no
      interfaces: 
         - enp1s0f0
         - enp1s0f1
      parameters:
        mode: balance-rr
  bridges:
    br0:
      interfaces: [bond0]
      dhcp4: no
      addresses: [10.1.10.10/24]
      gateway4: 10.1.10.1
      nameservers:
              addresses: [8.8.8.8,8.8.4.4][/FONT]

```

This was my first attempt, and gave some interesting results to say the least. Running netplan apply it took the config there were no errors however I only seem to have local connectivity at the server (no internet) and no connectivity to my VMs. When pinging the server (from a Windows client on wifi) every 10-11 pings I see latency jump to 200+ms for 1-3 packets then back to normal for the next 10 or so pings. Also when I fire up a VM and attempt to ping it, I get no response except for every 10 pings it returns one packet. I did not try pinging both at the same time to line up the timing but I'm pretty sure that isn't a coincidence. Both physical adapters are showing "UP" and packets in and out and it seems like the sum of the packets on both interfaces equals the packets sent/received on bond0. I have it back to using a single NIC for now but I would really like to figure out what I did wrong here.

---

### Post by kberdnikov-s on 2019-06-06
Did you solve this problem? With 
VIRTUALBOX it is enough to specify bond0 instead of br0 in the VM network settings. 
Unfortunately, lxc is not running opn bobd0. 
br0 does lost a part of packets of not see other hosts and as it seems to me a problem in arp table. 
I solved this problem by creating a static arp table. 
srv:/# arp -s host mac:address

---

### Post by nick-kostov on 2020-06-03
[COLOR=#000000]Check my [/COLOR][https://ubuntuforums.org/showthread....hlight=bonding]("https://ubuntuforums.org/showthread.php?t=2444718&highlight=bonding")[COLOR=#000000] .  
I fixed that by activating dhcp but still defining an IP address in the interfaces config.[/COLOR]

---

