---
title: "Activation: failed for connection"
date: 2019-02-19
forum: Networking &amp; Wireless
---

### Post by duncanmcl on 2019-02-19
I added two Quad Port Intel NIC cards to Ubuntu 18.10 desktop. There are a total of 9 Ethernet interfaces. I am getting lots of "Activation: failed for connection" notifications and the interfaces are getting down and up. Also the syslog shows lots of "failed to generate an address: Too many DAD collisions" messages. How can I solve this?

Below is the part of syslog that shows the problem
```
Feb 19 23:39:58 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587198.7138] device (enp6s0f1): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:39:58 Precision-Tower-3620-3 dhclient[6638]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 10 (xid=0x66fcbb5d)
Feb 19 23:39:59 Precision-Tower-3620-3 dhclient[6629]: DHCPDISCOVER on enp6s0f0 to 255.255.255.255 port 67 interval 11 (xid=0xabceb85e)
Feb 19 23:40:00 Precision-Tower-3620-3 dhclient[6646]: DHCPDISCOVER on enp6s0f1 to 255.255.255.255 port 67 interval 7 (xid=0xfb0e18)
Feb 19 23:40:07 Precision-Tower-3620-3 dhclient[6646]: DHCPDISCOVER on enp6s0f1 to 255.255.255.255 port 67 interval 15 (xid=0xfb0e18)
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587208.3736] dhcp4 (enp6s0f0): request timed out
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.3736] dhcp4 (enp6s0f0): state changed unknown -> timeout
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4060] dhcp4 (enp6s0f0): canceled DHCP transaction, DHCP client pid 6629
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4061] dhcp4 (enp6s0f0): state changed timeout -> done
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4065] device (enp6s0f0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587208.4075] device (enp6s0f0): Activation: failed for connection 'Wired connection 6'
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4079] device (enp6s0f0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4107] device (enp6s0f0): enslaved to non-master-type device ovs-system; ignoring
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4107] policy: auto-activating connection 'Wired connection 6' (09ddc0a3-4c71-3ef4-8ae1-1ce0c2ba012e)
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4118] device (enp6s0f0): Activation: starting connection 'Wired connection 6' (09ddc0a3-4c71-3ef4-8ae1-1ce0c2ba012e)
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4121] device (enp6s0f0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4129] device (enp6s0f0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4136] device (enp6s0f0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4142] dhcp4 (enp6s0f0): activation: beginning transaction (timeout in 45 seconds)
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4163] dhcp4 (enp6s0f0): dhclient started with pid 6652
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4193] device (enp6s0f0): ipv6: duplicate address check failed for the fe80::114e:a621:735c:c326/64 lft forever pref forever lifetime 7087-0[4294967295,4294967295] dev 3 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587208.4201] device (enp6s0f0): ipv6: duplicate address check failed for the fe80::e42e:ef9b:870f:11df/64 lft forever pref forever lifetime 7087-0[4294967295,4294967295] dev 3 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:08 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587208.4201] device (enp6s0f0): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:08 Precision-Tower-3620-3 dhclient[6638]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 10 (xid=0x66fcbb5d)
Feb 19 23:40:08 Precision-Tower-3620-3 dhclient[6652]: DHCPDISCOVER on enp6s0f0 to 255.255.255.255 port 67 interval 3 (xid=0x65505e0e)
Feb 19 23:40:09 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587209.5978] device (enp6s0f0): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:11 Precision-Tower-3620-3 dhclient[6652]: DHCPDISCOVER on enp6s0f0 to 255.255.255.255 port 67 interval 8 (xid=0x65505e0e)
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3728] policy: auto-activating connection 'Wired connection 9' (8fe10d42-2e1d-3ec3-96e4-7ba960e870f0)
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3737] device (enp7s0f1): Activation: starting connection 'Wired connection 9' (8fe10d42-2e1d-3ec3-96e4-7ba960e870f0)
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3739] device (enp7s0f1): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3747] device (enp7s0f1): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3758] device (enp7s0f1): enslaved to non-master-type device ovs-system; ignoring
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3759] device (enp7s0f1): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3766] dhcp4 (enp7s0f1): activation: beginning transaction (timeout in 45 seconds)
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3789] dhcp4 (enp7s0f1): dhclient started with pid 6662
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3828] device (enp7s0f1): ipv6: duplicate address check failed for the fe80::99d9:14a6:84c1:cac1/64 lft forever pref forever lifetime 7094-0[4294967295,4294967295] dev 6 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587215.3845] device (enp7s0f1): ipv6: duplicate address check failed for the fe80::192:ac59:ab36:1289/64 lft forever pref forever lifetime 7094-0[4294967295,4294967295] dev 6 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:15 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587215.3845] device (enp7s0f1): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:15 Precision-Tower-3620-3 dhclient[6662]: DHCPDISCOVER on enp7s0f1 to 255.255.255.255 port 67 interval 3 (xid=0xc6afe903)
Feb 19 23:40:17 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587217.1138] device (enp7s0f1): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:18 Precision-Tower-3620-3 dhclient[6662]: DHCPDISCOVER on enp7s0f1 to 255.255.255.255 port 67 interval 5 (xid=0xc6afe903)
Feb 19 23:40:18 Precision-Tower-3620-3 dhclient[6638]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 11 (xid=0x66fcbb5d)
Feb 19 23:40:19 Precision-Tower-3620-3 dhclient[6652]: DHCPDISCOVER on enp6s0f0 to 255.255.255.255 port 67 interval 11 (xid=0x65505e0e)
Feb 19 23:40:22 Precision-Tower-3620-3 dhclient[6646]: DHCPDISCOVER on enp6s0f1 to 255.255.255.255 port 67 interval 7 (xid=0xfb0e18)
Feb 19 23:40:23 Precision-Tower-3620-3 dhclient[6662]: DHCPDISCOVER on enp7s0f1 to 255.255.255.255 port 67 interval 10 (xid=0xc6afe903)
Feb 19 23:40:29 Precision-Tower-3620-3 dhclient[6646]: DHCPDISCOVER on enp6s0f1 to 255.255.255.255 port 67 interval 11 (xid=0xfb0e18)
Feb 19 23:40:29 Precision-Tower-3620-3 dhclient[6638]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 11 (xid=0x66fcbb5d)
Feb 19 23:40:30 Precision-Tower-3620-3 dhclient[6652]: DHCPDISCOVER on enp6s0f0 to 255.255.255.255 port 67 interval 16 (xid=0x65505e0e)
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587232.3816] dhcp4 (enp7s0f0): request timed out
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.3817] dhcp4 (enp7s0f0): state changed unknown -> timeout
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4139] dhcp4 (enp7s0f0): canceled DHCP transaction, DHCP client pid 6638
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4140] dhcp4 (enp7s0f0): state changed timeout -> done
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4143] device (enp7s0f0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587232.4153] device (enp7s0f0): Activation: failed for connection 'Wired connection 8'
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4158] device (enp7s0f0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4182] device (enp7s0f0): enslaved to non-master-type device ovs-system; ignoring
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4183] policy: auto-activating connection 'Wired connection 8' (52f859d2-e61b-3d30-9eaa-149cf8d97158)
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4194] device (enp7s0f0): Activation: starting connection 'Wired connection 8' (52f859d2-e61b-3d30-9eaa-149cf8d97158)
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4196] device (enp7s0f0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4204] device (enp7s0f0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4213] device (enp7s0f0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4219] dhcp4 (enp7s0f0): activation: beginning transaction (timeout in 45 seconds)
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4238] dhcp4 (enp7s0f0): dhclient started with pid 6672
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4270] device (enp7s0f0): ipv6: duplicate address check failed for the fe80::8d69:d114:be6c:fc4d/64 lft forever pref forever lifetime 7111-0[4294967295,4294967295] dev 5 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587232.4278] device (enp7s0f0): ipv6: duplicate address check failed for the fe80::32fd:f6f8:de9c:5bf1/64 lft forever pref forever lifetime 7111-0[4294967295,4294967295] dev 5 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:32 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587232.4278] device (enp7s0f0): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:32 Precision-Tower-3620-3 dhclient[6672]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 3 (xid=0xf42d8045)
Feb 19 23:40:33 Precision-Tower-3620-3 dhclient[6662]: DHCPDISCOVER on enp7s0f1 to 255.255.255.255 port 67 interval 19 (xid=0xc6afe903)
Feb 19 23:40:34 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587234.0737] device (enp7s0f0): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:35 Precision-Tower-3620-3 dhclient[6672]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 5 (xid=0xf42d8045)
Feb 19 23:40:40 Precision-Tower-3620-3 dhclient[6646]: DHCPDISCOVER on enp6s0f1 to 255.255.255.255 port 67 interval 13 (xid=0xfb0e18)
Feb 19 23:40:40 Precision-Tower-3620-3 dhclient[6672]: DHCPDISCOVER on enp7s0f0 to 255.255.255.255 port 67 interval 7 (xid=0xf42d8045)
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587242.3736] dhcp4 (enp6s0f1): request timed out
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.3736] dhcp4 (enp6s0f1): state changed unknown -> timeout
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4058] dhcp4 (enp6s0f1): canceled DHCP transaction, DHCP client pid 6646
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4059] dhcp4 (enp6s0f1): state changed timeout -> done
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4062] device (enp6s0f1): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587242.4071] device (enp6s0f1): Activation: failed for connection 'Wired connection 7'
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4075] device (enp6s0f1): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4100] device (enp6s0f1): enslaved to non-master-type device ovs-system; ignoring
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4101] policy: auto-activating connection 'Wired connection 7' (7ef89168-2470-386e-9b45-f6e998cd7393)
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4113] device (enp6s0f1): Activation: starting connection 'Wired connection 7' (7ef89168-2470-386e-9b45-f6e998cd7393)
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4115] device (enp6s0f1): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4123] device (enp6s0f1): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4131] device (enp6s0f1): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4136] dhcp4 (enp6s0f1): activation: beginning transaction (timeout in 45 seconds)
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4172] dhcp4 (enp6s0f1): dhclient started with pid 6702
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4239] device (enp6s0f1): ipv6: duplicate address check failed for the fe80::d3a3:8cd4:f2d6:f9b4/64 lft forever pref forever lifetime 7121-0[4294967295,4294967295] dev 4 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <info>  [1550587242.4250] device (enp6s0f1): ipv6: duplicate address check failed for the fe80::539b:ac14:1272:5277/64 lft forever pref forever lifetime 7121-0[4294967295,4294967295] dev 4 flags permanent,noprefixroute,tentative src kernel address
Feb 19 23:40:42 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587242.4251] device (enp6s0f1): linklocal6: failed to generate an address: Too many DAD collisions
Feb 19 23:40:42 Precision-Tower-3620-3 dhclient[6702]: DHCPDISCOVER on enp6s0f1 to 255.255.255.255 port 67 interval 3 (xid=0x98a7e370)
Feb 19 23:40:43 Precision-Tower-3620-3 NetworkManager[879]: <warn>  [1550587243.8378] device (enp6s0f1): linklocal6: failed to generate an address: Too many DAD collisions
```

---

