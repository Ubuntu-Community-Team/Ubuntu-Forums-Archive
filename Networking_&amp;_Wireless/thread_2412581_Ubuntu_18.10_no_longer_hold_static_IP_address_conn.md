---
title: "Ubuntu 18.10 no longer hold static IP address connection"
date: 2019-02-14
forum: Networking &amp; Wireless
---

### Post by mike.lussier on 2019-02-14
This has started in the past 24 hours. I loos my internet connection from this machine. if I switch up to DHCP I can then switch back to static . I'm running some apps that are setup to a static IP I can't be switching to DHCP to make this work. local network 
This is a HP desktop 
```
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.20.26  netmask 255.255.255.0  broadcast 192.168.20.255
        inet6 fe80::d6c9:efff:fef4:e589  prefixlen 64  scopeid 0x20<link>
        ether d4:c9:ef:f4:e5:89  txqueuelen 1000  (Ethernet)
        RX packets 68441  bytes 58509104 (58.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 51821  bytes 7902148 (7.9 MB)
        TX errors 31  dropped 0 overruns 0  carrier 31  collisions 7557
        device interrupt 20  memory 0xf7100000-f7120000  


Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.0154] device (eno1): disconnecting for new activation request.
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.0154] device (eno1): state change: activated -> deactivating (reason 'new-activation', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.0897] device (eno1): state change: deactivating -> disconnected (reason 'new-activation', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Withdrawing address record for fe80::d6c9:efff:fef4:e589 on eno1.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Leaving mDNS multicast group on interface eno1.IPv6 with address fe80::d6c9:efff:fef4:e589.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Interface eno1.IPv6 no longer relevant for mDNS.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Withdrawing address record for 192.168.20.26 on eno1.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Leaving mDNS multicast group on interface eno1.IPv4 with address 192.168.20.26.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Interface eno1.IPv4 no longer relevant for mDNS.
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.1265] device (eno1): Activation: starting connection 'Master' (57a351d3-9e70-45ce-995f-5bf78fe0f46f)
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.1279] device (eno1): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.1447] device (eno1): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.1490] device (eno1): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.1493] dhcp4 (eno1): activation: beginning transaction (timeout in 45 seconds)
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.1506] dhcp4 (eno1): dhclient started with pid 12883
Feb 14 17:50:40 ae4ml-DeskComputer nm-dispatcher: req:1 'down' [eno1]: new request (2 scripts)
Feb 14 17:50:40 ae4ml-DeskComputer nm-dispatcher: req:1 'down' [eno1]: start running ordered scripts...
Feb 14 17:50:40 ae4ml-DeskComputer dhclient[12883]: DHCPREQUEST of 192.168.20.1 on eno1 to 255.255.255.255 port 67 (xid=0x1abec3de)
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   address 192.168.20.1
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   plen 24 (255.255.255.0)
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   gateway 192.168.20.254
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   lease time 3600
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   nameserver '172.17.2.1'
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   nameserver '8.8.8.8'
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2329] dhcp4 (eno1):   nameserver '8.8.4.4'
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2330] dhcp4 (eno1):   domain name 'ae4ml.ham'
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2330] dhcp4 (eno1): state changed unknown -> bound
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Joining mDNS multicast group on interface eno1.IPv4 with address 192.168.20.1.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: New relevant interface eno1.IPv4 for mDNS.
Feb 14 17:50:40 ae4ml-DeskComputer avahi-daemon[1798]: Registering new address record for 192.168.20.1 on eno1.IPv4.
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2387] device (eno1): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2393] device (eno1): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.2394] device (eno1): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.3264] policy: set 'Master' (eno1) as default for IPv4 routing and DNS
Feb 14 17:50:40 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184640.3269] device (eno1): Activation: successful, device activated.
Feb 14 17:50:40 ae4ml-DeskComputer nm-dispatcher: req:2 'up' [eno1]: new request (2 scripts)
Feb 14 17:50:40 ae4ml-DeskComputer nm-dispatcher: req:2 'up' [eno1]: start running ordered scripts...
Feb 14 17:50:42 ae4ml-DeskComputer avahi-daemon[1798]: Joining mDNS multicast group on interface eno1.IPv6 with address fe80::d6c9:efff:fef4:e589.
Feb 14 17:50:42 ae4ml-DeskComputer avahi-daemon[1798]: New relevant interface eno1.IPv6 for mDNS.
Feb 14 17:50:42 ae4ml-DeskComputer avahi-daemon[1798]: Registering new address record for fe80::d6c9:efff:fef4:e589 on eno1.*.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.4704] device (eno1): disconnecting for new activation request.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.4705] device (eno1): state change: activated -> deactivating (reason 'new-activation', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5319] device (eno1): state change: deactivating -> disconnected (reason 'new-activation', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Withdrawing address record for fe80::d6c9:efff:fef4:e589 on eno1.
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Leaving mDNS multicast group on interface eno1.IPv6 with address fe80::d6c9:efff:fef4:e589.
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Interface eno1.IPv6 no longer relevant for mDNS.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5426] dhcp4 (eno1): canceled DHCP transaction, DHCP client pid 12883
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5427] dhcp4 (eno1): state changed bound -> done
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Withdrawing address record for 192.168.20.1 on eno1.
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Leaving mDNS multicast group on interface eno1.IPv4 with address 192.168.20.1.
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Interface eno1.IPv4 no longer relevant for mDNS.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5467] device (eno1): Activation: starting connection '192.168.20.26' (9f810fa9-a709-4704-a94a-c1e4fc8b2d87)
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5479] device (eno1): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5483] device (eno1): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5518] device (eno1): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer nm-dispatcher: req:2 'down' [eno1]: new request (2 scripts)
Feb 14 17:50:56 ae4ml-DeskComputer nm-dispatcher: req:2 'down' [eno1]: start running ordered scripts...
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Joining mDNS multicast group on interface eno1.IPv4 with address 192.168.20.26.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5766] device (eno1): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: New relevant interface eno1.IPv4 for mDNS.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5775] device (eno1): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer avahi-daemon[1798]: Registering new address record for 192.168.20.26 on eno1.IPv4.
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.5776] device (eno1): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.6251] policy: set '192.168.20.26' (eno1) as default for IPv4 routing and DNS
Feb 14 17:50:56 ae4ml-DeskComputer NetworkManager[1813]: <info>  [1550184656.6260] device (eno1): Activation: successful, device activated.
Feb 14 17:50:56 ae4ml-DeskComputer nm-dispatcher: req:3 'up' [eno1]: new request (2 scripts)
Feb 14 17:50:56 ae4ml-DeskComputer nm-dispatcher: req:3 'up' [eno1]: start running ordered scripts...
Feb 14 17:50:58 ae4ml-DeskComputer avahi-daemon[1798]: Joining mDNS multicast group on interface eno1.IPv6 with address fe80::d6c9:efff:fef4:e589.
Feb 14 17:50:58 ae4ml-DeskComputer avahi-daemon[1798]: New relevant interface eno1.IPv6 for mDNS.
Feb 14 17:50:58 ae4ml-DeskComputer avahi-daemon[1798]: Registering new address record for fe80::d6c9:efff:fef4:e589 on eno1.*.
```

---

### Post by chili555 on 2019-02-14
Where did you set the static IP? Network Manager or elsewhere?

---

### Post by mike.lussier on 2019-02-15
network manager, 
Im having to bounce between a static IP and DHCP about every 10 minutes or I loose internet connectivity

---

### Post by chili555 on 2019-02-15
Did you make quite sure to select a static IP outside the DHCP pool?

Are you confident that the static IP accounts for the instability? Could it be Network Manager? Power saving?

Is this the static IP you set?> 
Registering new address record for 192.168.20.1 
Typically, x.1 is otherwise reserved.

---

### Post by mike.lussier on 2019-02-16
I have always used the high end address for router 20.254 so yes 20.1 is valid device IP address. That is a dhcp address . The address on the desktop is 20.26 of which it has been for years. I have put in place a brand new ethernet PCIE card. The computer recognized it and I disabled the onboard card and assigned an ip to the new card.  Exactly the same behavior as the onboard card.  Its frustrating but I think that rules out a hardware issue.

---

### Post by mike.lussier on 2019-02-16
Chili555,
There is no power save mode is in place on this machine

---

### Post by mike.lussier on 2019-02-16
The problem isn't IP address or network card. as much as /etc/resolv.conf is being wiped out and an address of 127.0.0.53 is the only entry in the file. I have no dns resolution.

---

### Post by chili555 on 2019-02-16
What does this tell us?```
ls -al /etc/resolv.conf
```We hope it is:```
lrwxrwxrwx 1 root root 39 Jul 15  2018 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

```Or maybe: ```
lrwxrwxrwx 1 root root 39 Jul 15  2018 /etc/resolv.conf -> ../run/systemd/resolve/resolv.conf

```Since resolution seems to work with DHCP but not static, that suggests that the DNS nameservers were not correct or not set at all under static.

---

