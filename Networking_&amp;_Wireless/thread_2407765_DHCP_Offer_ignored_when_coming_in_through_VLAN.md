---
title: "DHCP Offer ignored when coming in through VLAN"
date: 2018-12-09
forum: Networking &amp; Wireless
---

### Post by bartgrefte on 2018-12-09
Recently I set up a VLAN that will be used by guests once I get an access point with guest network functionality.

To test the VLAN-setup, I configured the ASIX AX88179 USB3-Gb network adapter hooked to my laptop to use the configured VLAN ID I set at my router-pc and on the switch.

If I do this on W7 and W10, no problems, both get an IP-address in the guest-network range. If I do the same on Kubuntu 18.10 (triple boot) then the DHCP Offer package is ignored.

I know it arrives after Kubuntu sends the DHCP Discover package, checked that with Wireshark, but Kubuntu doesn't seem to be able to pick it up, at least I do not think so:
```
dec 08 16:46:34 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 5 (xid=0x6f4fe067)
dec 08 16:46:41 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 8 (xid=0x6f4fe067)
dec 08 16:46:49 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 16 (xid=0x6f4fe067)
dec 08 16:47:05 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 10 (xid=0x6f4fe067)
dec 08 16:47:15 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 8 (xid=0x6f4fe067)
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <warn>  [1544284039.4254] dhcp4 (enx00249b138.50): request timed out
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4254] dhcp4 (enx00249b138.50): state changed unknown -> timeout
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4575] dhcp4 (enx00249b138.50): canceled DHCP transaction, DHCP client pid 3008
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4576] dhcp4 (enx00249b138.50): state changed timeout -> done
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4580] device (enx00249b138.50): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <warn>  [1544284039.4592] device (enx00249b138.50): Activation: failed for connection 'vlan50'
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4596] device (enx00249b138.50): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Withdrawing address record for fe80::224:9bff:fe13:897e on enx00249b138.50.
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Leaving mDNS multicast group on interface enx00249b138.50.IPv6 with address fe80::224:9bff:fe13:897e.
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Interface enx00249b138.50.IPv6 no longer relevant for mDNS.
```
There are no problems on the untagged interface, that one gets an IP-address (from a different range) without any problems.

Since the DHCP server-config used on the VLAN is exactly the same as the config used on the untagged network (minus the IP-range that is), since it works on W7 and W10 and since the DHCP Offer package arrives, I don't think it's going wrong at the DHCP server.

I don't suppose anyone can give me some clues as to where to look for the cause?

---

### Post by mitesh.agrwl on 2018-12-09
> **bartgrefte said:**
> Recently I set up a VLAN that will be used by guests once I get an access point with guest network functionality.

To test the VLAN-setup, I configured the ASIX AX88179 USB3-Gb network adapter hooked to my laptop to use the configured VLAN ID I set at my router-pc and on the switch.

If I do this on W7 and W10, no problems, both get an IP-address in the guest-network range. If I do the same on Kubuntu 18.10 (triple boot) then the DHCP Offer package is ignored.

I know it arrives after Kubuntu sends the DHCP Discover package, checked that with Wireshark, but Kubuntu doesn't seem to be able to pick it up, at least I do not think so:
```
dec 08 16:46:34 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 5 (xid=0x6f4fe067)
dec 08 16:46:41 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 8 (xid=0x6f4fe067)
dec 08 16:46:49 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 16 (xid=0x6f4fe067)
dec 08 16:47:05 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 10 (xid=0x6f4fe067)
dec 08 16:47:15 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 8 (xid=0x6f4fe067)
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <warn>  [1544284039.4254] dhcp4 (enx00249b138.50): request timed out
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4254] dhcp4 (enx00249b138.50): state changed unknown -> timeout
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4575] dhcp4 (enx00249b138.50): canceled DHCP transaction, DHCP client pid 3008
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4576] dhcp4 (enx00249b138.50): state changed timeout -> done
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4580] device (enx00249b138.50): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <warn>  [1544284039.4592] device (enx00249b138.50): Activation: failed for connection 'vlan50'
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4596] device (enx00249b138.50): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Withdrawing address record for fe80::224:9bff:fe13:897e on enx00249b138.50.
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Leaving mDNS multicast group on interface enx00249b138.50.IPv6 with address fe80::224:9bff:fe13:897e.
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Interface enx00249b138.50.IPv6 no longer relevant for mDNS.
```
There are no problems on the untagged interface, that one gets an IP-address (from a different range) without any problems.

Since the DHCP server-config used on the VLAN is exactly the same as the config used on the untagged network (minus the IP-range that is), since it works on W7 and W10 and since the DHCP Offer package arrives, I don't think it's going wrong at the DHCP server.

I don't suppose anyone can give me some clues as to where to look for the cause?

From the description above, it does it seems to be the host/DHCP client (Kubutu) problem. It is not receiving any DHCP offer to ignore. Please make sure that the DHCP server is receiving the client request and processing it properly and sending out the Offer packet. It it is so, it is needed to ensure that the Offer packet is received on Kubuntu PC, receiving packet and ignoring/rejecting it are two different process, if the packet is received only then it can be figured out why it is ignored/rejected.

When there is no VLAN, the packet is received in native VLAN, and the client is getting IP address from the DHCP server pool active for native VLAN.

---

### Post by bartgrefte on 2018-12-10
> **mitesh.agrwl said:**
> From the description above, it does it seems to be the host/DHCP client (Kubutu) problem. It is not receiving any DHCP offer to ignore. Please make sure that the DHCP server is receiving the client request and processing it properly and sending out the Offer packet. It it is so, it is needed to ensure that the Offer packet is received on Kubuntu PC, receiving packet and ignoring/rejecting it are two different process, if the packet is received only then it can be figured out why it is ignored/rejected.
As I already said ;) , I checked with Wireshark to see if the DHCP Offer package arrives as a response to Kubuntu's DHCP Discover package, it does and contains all required data: The offered IP-address in the guest network range, the IP-address of the router's VLAN-interface, DNS-server, etc.

> **mitesh.agrwl said:**
>  When there is no VLAN, the packet is received in native VLAN, and the client is getting IP address from the DHCP server pool active for native VLAN. 
Yes and that works, with the exact same DHCP-server config, though a different range: 192.168.1.* (untagged/native VLAN) instead of 192.168.3.* (tagged VLAN).

There is one other difference though, I doubt it matters since Windows 7 and 10 don't see it as a problem (although, Kubuntu might). On the guest network, the IP-address of the router/gateway is different from that of the DHCP-server. 

I'm using IPFire as a router and IPFire has some annoying limitations, one of those limitations is the reason that the DHCP-server for VLAN is running on a different device (Raspberry Pi). Please don't tell me the DHCP client requires the router-IP to be the same as that of the DHCP server?

---

### Post by mitesh.agrwl on 2018-12-10
> As I already said :wink:  , I checked with Wireshark to see if the DHCP Offer package arrives as a  response to Kubuntu's DHCP Discover package, it does and contains all  required data: The offered IP-address in the guest network range, the  IP-address of the router's VLAN-interface, DNS-server, etc.

But the output from your previous post does not suggest so.

> ```
dec 08 16:46:34 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 5 (xid=0x6f4fe067)
dec 08 16:46:41 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 8 (xid=0x6f4fe067)
dec 08 16:46:49 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 16 (xid=0x6f4fe067)
dec 08 16:47:05 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 10 (xid=0x6f4fe067)
dec 08 16:47:15 Kubuntu dhclient[3008]: DHCPDISCOVER on enx00249b138.50 to 255.255.255.255 port 67 interval 8 (xid=0x6f4fe067)
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <warn>  [1544284039.4254] dhcp4 (enx00249b138.50): request timed out
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4254] dhcp4 (enx00249b138.50): state changed unknown -> timeout
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4575] dhcp4 (enx00249b138.50): canceled DHCP transaction, DHCP client pid 3008
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4576] dhcp4 (enx00249b138.50): state changed timeout -> done
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4580] device (enx00249b138.50): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <warn>  [1544284039.4592] device (enx00249b138.50): Activation: failed for connection 'vlan50'
dec 08 16:47:19 Kubuntu NetworkManager[1139]: <info>  [1544284039.4596] device (enx00249b138.50): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Withdrawing address record for fe80::224:9bff:fe13:897e on enx00249b138.50.
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Leaving mDNS multicast group on interface enx00249b138.50.IPv6 with address fe80::224:9bff:fe13:897e.
dec 08 16:47:19 Kubuntu avahi-daemon[1239]: Interface enx00249b138.50.IPv6 no longer relevant for mDNS.
```

The reason mentioned here is ***request time out*** by Network Manager for DHCP.

can you post the output of ```
$dhclient -v
```

---

### Post by bartgrefte on 2018-12-11
> **mitesh.agrwl said:**
> But the output from your previous post does not suggest so.

The reason mentioned here is ***request time out*** by Network Manager for DHCP.

can you post the output of ```
$dhclient -v
```
Well, then who's to believe, Wireshark that indicates it arrives or the DHCP-server that doesn't seem to pick it up?

But I've managed to work around the problem. I disabled the graphical Network Manager and switched to configuring the (virtual) interfaces in /etc/network/interfaces, no problems there, DHCP over VLAN immediately worked :) .... once I figured out to use vlan50 instead of namephysicalinterface.50, the latter wasn't accepted in /etc/network/interfaces:
"Error: argument "namephysicalinterface.50" is wrong: "name" not a valid ifname".
edit: That error might have been caused by [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1567744](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1567744) , the length is apparently an issue.

---

