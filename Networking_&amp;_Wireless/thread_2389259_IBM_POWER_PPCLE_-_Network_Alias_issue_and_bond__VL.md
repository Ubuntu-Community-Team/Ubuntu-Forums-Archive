---
title: "IBM POWER PPCLE - Network Alias issue and bond / VLAN configuation"
date: 2018-04-13
forum: Networking &amp; Wireless
---

### Post by penguinpages2 on 2018-04-13
Not new to linux but to Ubuntu as a distribution to use in production.

Trying to build a production class (NSPOF) KVM server with Ubuntu server 16.0.4.4ppc le

Installation goes fine (draft guide I will post .. if forum allows for space..once I get last few things cleaned up).

Down now to networking.. so I can get to fun part of bringing it under POWERVC (IBM's version of Open Stack IAAS control) then into ICP (IBM's version of Kubernetes)

.. i digress...


Issue:
1) Too many googling / forums / differnt documentation sites.. none of which articulate what is needed for KVM NSPOF.. Bond.. with interfaces across two switches, and to that bind VLANs.  Switch is simple "Trunk allow vlan all"   so KVM can create VLANs (public / private etc) as needed.

2) I had to manually construct device aliases for udev... but still does not do a clean job of managment of interfaces.   "systemclt stop networking" does not shut down intefaces..  I can do a "ifdown bond0" and it shuts down the logical interface and subsequent slave interfaces..   This needs some cleanup.


Attached is a dmeg output of clean boot, as well as draft of "how I did it"  and so should articulate full story.

What I need is correction to stanzas of vlans  (some with and most without IP bound).. bound to bond.

 
[TABLE]
[TR]
[TD]root@l8247l1p1:~# sudo vi /etc/network/interfaces
[/TD]
[TD]Switch side:  Ex Brocade VDX 6740
[/TD]
[/TR]
[TR]
[TD]# and how to activate them. For more information, see interfaces(5).
 
source /etc/network/interfaces.d/*
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
 
#enP4p1s0f0 configuration sw26-10
auto enP4p1s0f0
iface enP4p1s0f0 inet manual
bond-master bond0
 
#enP5p9s0f1 configuration sw20-09
auto enP5p9s0f1
iface enP5p9s0f1 inet manual
bond-master bond0
 
# bond0 is the bonded NIC for VM and Mgmt traffic
auto bond0
iface bond0 inet manual
# bond0 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves enP4p1s0f0 enP5p9s0f1
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
 
auto bond0.11
iface bond0.11 inet static
address 172.20.11.131
gateway 202.1.2.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8
vlan-raw-device bond0
 
######
 
#enP4p1s0f1 configuration sw20-10
auto enP4p1s0f1
iface enP4p1s0f1 inet manual
bond-master bond1
 
#enP5p9s0f0 configuration sw26-09
auto enP5p9s0f0
iface enP5p9s0f0 inet manual
bond-master bond1
 
# bond1 is the bonded NIC for iSCSI traffic
# bond1 is used by VMs for block traffic
auto bond1
iface bond1 inet manual
# bond1 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves enP4p1s0f1 enP5p9s0f0
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
 
auto bond1.19
iface bond1.19 inet static
address 172.20.19.250
gateway 172.20.19.1
netmask 255.255.255.0
dns-nameservers 172.20.12.100
vlan-raw-device bond1
[/TD]
[TD]!
interface Port-channel 23
 vlag ignore-split
 mtu 9028
 description l8247l1p1_bond0
 switchport
 switchport mode trunk
 switchport trunk allowed vlan all
no  switchport trunk tag native-vlan
no  switchport trunk native-vlan 11
 spanning-tree shutdown
no shutdown
!
interface Port-channel 24
 vlag ignore-split
 mtu 9028
 description l8247l1p1_bond1
 switchport
 switchport mode trunk
 switchport trunk allowed vlan all
no switchport trunk tag native-vlan
no switchport trunk native-vlan 11
 spanning-tree shutdown
 no shutdown
!
interface TenGigabitEthernet 26/0/10
 description  l8247l1p1_enP4p1s0f0
 channel-group 23 mode active type standard
 fabric isl enable
 fabric trunk enable
 lacp timeout long
 storm-control ingress broadcast limit-percent 5 monitor
 storm-control ingress multicast limit-percent 5 monitor
 storm-control ingress unknown-unicast limit-percent 5 monitor
 no shutdown
!
interface TenGigabitEthernet 20/0/9
 description  l8247l1p1_enP5p9s0f1
 channel-group 23 mode active type standard
 fabric isl enable
 fabric trunk enable
 lacp timeout long
 storm-control ingress broadcast limit-percent 5 monitor
 storm-control ingress multicast limit-percent 5 monitor
 storm-control ingress unknown-unicast limit-percent 5 monitor
no shutdown
!
interface TenGigabitEthernet 20/0/10
 description  l8247l1p1_enP4p1s0f1
 channel-group 24 mode active type standard
 fabric isl enable
 fabric trunk enable
 lacp timeout long
 storm-control ingress broadcast limit-percent 5 monitor
 storm-control ingress multicast limit-percent 5 monitor
 storm-control ingress unknown-unicast limit-percent 5 monitor
 no shutdown
!
interface TenGigabitEthernet 26/0/9
 description  l8247l1p1_enP5p9s0f0
 channel-group 24 mode active type standard
 fabric isl enable
 fabric trunk enable
 lacp timeout long
 storm-control ingress broadcast limit-percent 5 monitor
 storm-control ingress multicast limit-percent 5 monitor
 storm-control ingress unknown-unicast limit-percent 5 monitor
no shutdown
 
[/TD]
[/TR]
[/TABLE]

---

### Post by penguinpages2 on 2018-04-16
Update... still not working but more to go on...  I found some other postings which seem to clean up the configuration file..  it no longer gives errors on clean boot / systemctl restart networking.service

```
Configuration:
#############
root@l82471p1:~# cat /etc/network/interfaces
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface


#enP4p1s0f0 configuration sw26-10
auto enP4p1s0f0
iface enP4p1s0f0 inet manual
bond-master bond0


#enP5p9s0f1 configuration sw20-09
auto enP5p9s0f1
iface enP5p9s0f1 inet manual
bond-master bond0


# bond0 is the bonded NIC for VM and Mgmt traffic
auto bond0
iface bond0 inet manual
# bond0 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves enP4p1s0f0 enP5p9s0f1
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1


# Create VLAN interface to bond0
# auto bond1.11
# iface bond1.11 inet manual


auto virbr11
iface virbr11 inet static
        address 172.20.11.131
        netmask 255.255.255.0
        broadcast 172.20.11.255
        network 172.20.11.0
        vlan-raw-device bond0
        bridge_ports bond0.11
        bridge_stp off


######


#enP4p1s0f1 configuration sw20-10
auto enP4p1s0f1
iface enP4p1s0f1 inet manual
bond-master bond1


#enP5p9s0f0 configuration sw26-09
auto enP5p9s0f0
iface enP5p9s0f0 inet manual
bond-master bond1


# bond1 is the bonded NIC for iSCSI traffic
# bond1 is used by VMs for block traffic
auto bond1
iface bond1 inet manual
# bond1 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves enP4p1s0f1 enP5p9s0f0
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1


auto virbr19
iface virbr19 inet static
        address 172.20.19.251
        netmask 255.255.255.0
        broadcast 172.20.19.255
        network 172.20.19.0
        vlan-raw-device bond0
        bridge_ports bond1.19
        bridge_stp off
root@l82471p1:~# cat /etc/network/interfaces
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface


#enP4p1s0f0 configuration sw26-10
auto enP4p1s0f0
iface enP4p1s0f0 inet manual
bond-master bond0


#enP5p9s0f1 configuration sw20-09
auto enP5p9s0f1
iface enP5p9s0f1 inet manual
bond-master bond0


# bond0 is the bonded NIC for VM and Mgmt traffic
auto bond0
iface bond0 inet manual
# bond0 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves enP4p1s0f0 enP5p9s0f1
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1


# Create VLAN interface to bond0
# auto bond1.11
# iface bond1.11 inet manual


auto virbr11
iface virbr11 inet static
        address 172.20.11.131
        netmask 255.255.255.0
        broadcast 172.20.11.255
        network 172.20.11.0
        vlan-raw-device bond0
        bridge_ports bond0.11
        bridge_stp off


######


#enP4p1s0f1 configuration sw20-10
auto enP4p1s0f1
iface enP4p1s0f1 inet manual
bond-master bond1


#enP5p9s0f0 configuration sw26-09
auto enP5p9s0f0
iface enP5p9s0f0 inet manual
bond-master bond1


# bond1 is the bonded NIC for iSCSI traffic
# bond1 is used by VMs for block traffic
auto bond1
iface bond1 inet manual
# bond1 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves enP4p1s0f1 enP5p9s0f0
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1


auto virbr19
iface virbr19 inet static
        address 172.20.19.251
        netmask 255.255.255.0
        broadcast 172.20.19.255
        network 172.20.19.0
        vlan-raw-device bond0
        bridge_ports bond1.19
        bridge_stp off



############



The bond seems to link and can see the switch KEY ID on the bond:
#######Ex bond 0 to switch po 23##########

root@l82471p1:~# cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer3+4 (1)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0


802.3ad info
LACP rate: fast
Min links: 0
Aggregator selection policy (ad_select): stable
System priority: 65535
System MAC address: 98:be:94:59:fe:a0
Active Aggregator Info:
        Aggregator ID: 1
        Number of ports: 2
        Actor Key: 15
        Partner Key: 23
        Partner Mac Address: 01:e0:52:00:00:0c


Slave Interface: enP4p1s0f0
MII Status: up
Speed: 10000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 98:be:94:59:fe:a0
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 0
Partner Churned Count: 0
details actor lacp pdu:
    system priority: 65535
    system mac address: 98:be:94:59:fe:a0
    port key: 15
    port priority: 255
    port number: 1
    port state: 63
details partner lacp pdu:
    system priority: 32768
    system mac address: 01:e0:52:00:00:0c
    oper key: [COLOR=#ff0000]23[/COLOR]
    port priority: 32768
    port number: 13322
    port state: 61


Slave Interface: enP5p9s0f1
MII Status: up
Speed: 10000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 98:be:94:59:fe:11
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 0
Partner Churned Count: 0
details actor lacp pdu:
    system priority: 65535
    system mac address: 98:be:94:59:fe:a0
    port key: 15
    port priority: 255
    port number: 2
    port state: 63
details partner lacp pdu:
    system priority: 32768
    system mac address: 01:e0:52:00:00:0c
    oper key: 23
    port priority: 32768
    port number: 10249
    port state: 61
root@l82471p1:~#
root@l82471p1:~# cat /proc/net/vlan/config
VLAN Dev name    | VLAN ID
Name-Type: VLAN_NAME_TYPE_RAW_PLUS_VID_NO_PAD
rename25       | 11  | bond0
rename28       | 19  | bond1
root@l82471p1:~#
root@l82471p1:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.20.11.0     *               255.255.255.0   U     0      0        0 virbr11
172.20.19.0     *               255.255.255.0   U     0      0        0 virbr19
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
root@l82471p1:~#




#################################

root@l82471p1:~# cat /var/log/syslog
foo
Apr 16 09:16:55 l82471p1 systemd[1]: Stopping Raise network interfaces...
Apr 16 09:16:55 l82471p1 rsyslogd-2007: action 'action 10' suspended, next retry is Mon Apr 16 09:17:25 2018 [v8.16.0 try [http://www.rsyslog.com/e/2007](http://www.rsyslog.com/e/2007) ]
Apr 16 09:16:55 l82471p1 systemd[1]: Stopping ifup for virbr19...
Apr 16 09:16:55 l82471p1 ifdown[6616]: /sbin/ifdown: waiting for lock on /run/network/ifstate.virbr19
Apr 16 09:16:55 l82471p1 ifdown[6578]: ERROR: trying to remove VLAN -:virbr19:- error: No such device
Apr 16 09:16:55 l82471p1 ifdown[6578]: run-parts: /etc/network/if-post-down.d/vlan exited with return code 4
Apr 16 09:16:55 l82471p1 ifdown[6616]: /sbin/ifdown: interface virbr19 not configured
Apr 16 09:16:55 l82471p1 systemd[1]: Stopped ifup for virbr19.
Apr 16 09:16:55 l82471p1 kernel: [  286.136915] bond1: Removing slave enP5p9s0f0
Apr 16 09:16:55 l82471p1 kernel: [  286.137242] bond1: Releasing active interface enP5p9s0f0
Apr 16 09:16:55 l82471p1 ifdown[6578]: enP4p1s0f1=enP4p1s0f1
Apr 16 09:16:55 l82471p1 kernel: [  286.771043] bond1: link status definitely down for interface enP4p1s0f1, disabling it
Apr 16 09:16:55 l82471p1 kernel: [  286.771056] bond1: now running without any active interface!
Apr 16 09:16:55 l82471p1 kernel: [  286.772435] bond1: Removing slave enP4p1s0f1
Apr 16 09:16:55 l82471p1 kernel: [  286.772781] bond1: Releasing backup interface enP4p1s0f1
Apr 16 09:16:55 l82471p1 kernel: [  286.792447] bonding: bond1 is being deleted...
Apr 16 09:16:55 l82471p1 kernel: [  286.807719] bond1 (unregistering): Released all slaves
Apr 16 09:16:55 l82471p1 systemd[1]: Stopping ifup for bond1...
Apr 16 09:16:55 l82471p1 ifdown[6684]: /sbin/ifdown: waiting for lock on /run/network/ifstate.bond1
Apr 16 09:16:55 l82471p1 ifdown[6684]: /sbin/ifdown: interface bond1 not configured
Apr 16 09:16:55 l82471p1 systemd[1]: Stopped ifup for bond1.
Apr 16 09:16:56 l82471p1 kernel: [  286.873263] bond0: Removing slave enP5p9s0f1
Apr 16 09:16:56 l82471p1 kernel: [  286.873660] bond0: Releasing active interface enP5p9s0f1
Apr 16 09:16:56 l82471p1 ifdown[6578]: ERROR: trying to remove VLAN -:virbr11:- error: No such device
Apr 16 09:16:56 l82471p1 ifdown[6578]: run-parts: /etc/network/if-post-down.d/vlan exited with return code 4
Apr 16 09:16:56 l82471p1 systemd[1]: Stopping ifup for virbr11...
Apr 16 09:16:56 l82471p1 ifdown[6733]: /sbin/ifdown: interface virbr11 not configured
Apr 16 09:16:56 l82471p1 systemd[1]: Stopped ifup for virbr11.
Apr 16 09:16:56 l82471p1 ifdown[6578]: enP4p1s0f0=enP4p1s0f0
Apr 16 09:16:56 l82471p1 kernel: [  287.643030] bond0: link status definitely down for interface enP4p1s0f0, disabling it
Apr 16 09:16:56 l82471p1 kernel: [  287.643038] bond0: now running without any active interface!
Apr 16 09:16:56 l82471p1 kernel: [  287.645430] bond0: Removing slave enP4p1s0f0
Apr 16 09:16:56 l82471p1 kernel: [  287.645779] bond0: Releasing backup interface enP4p1s0f0
Apr 16 09:16:56 l82471p1 kernel: [  287.660545] bonding: bond0 is being deleted...
Apr 16 09:16:56 l82471p1 kernel: [  287.667446] bond0 (unregistering): Released all slaves
Apr 16 09:16:56 l82471p1 systemd[1]: Stopping ifup for bond0...
Apr 16 09:16:56 l82471p1 ifdown[6784]: /sbin/ifdown: waiting for lock on /run/network/ifstate.bond0
Apr 16 09:16:56 l82471p1 ifdown[6784]: /sbin/ifdown: interface bond0 not configured
Apr 16 09:16:56 l82471p1 systemd[1]: Stopped ifup for bond0.
Apr 16 09:16:56 l82471p1 systemd[1]: Stopped Raise network interfaces.
Apr 16 09:16:56 l82471p1 systemd[1]: Starting Raise network interfaces...
Apr 16 09:16:56 l82471p1 ifup[6803]: Waiting for bond master bond0 to be ready
Apr 16 09:16:56 l82471p1 systemd-udevd[6818]: Could not generate persistent MAC address for bond0: No such file or directory
Apr 16 09:16:56 l82471p1 kernel: [  287.732647] bonding: bond0 is being created...
Apr 16 09:16:56 l82471p1 kernel: [  287.749338] bond0: Setting xmit hash policy to layer3+4 (1)
Apr 16 09:16:56 l82471p1 kernel: [  287.749438] bond0: Setting MII monitoring interval to 100
Apr 16 09:16:56 l82471p1 kernel: [  287.749509] bond0: Setting down delay to 0
Apr 16 09:16:56 l82471p1 kernel: [  287.749580] bond0: Setting up delay to 0
Apr 16 09:16:56 l82471p1 kernel: [  287.753096] bond0: Setting LACP rate to fast (1)
Apr 16 09:16:56 l82471p1 kernel: [  287.753568] IPv6: ADDRCONF(NETDEV_UP): bond0: link is not ready
Apr 16 09:16:56 l82471p1 kernel: [  287.753571] 8021q: adding VLAN 0 to HW filter on device bond0
Apr 16 09:16:56 l82471p1 kernel: [  287.836574] bond0: Adding slave enP4p1s0f0
Apr 16 09:16:57 l82471p1 kernel: [  288.351827] bnx2x 0004:01:00.0 enP4p1s0f0: using MSI-X  IRQs: sp 455  fp[0] 457 ... fp[7] 464
Apr 16 09:16:57 l82471p1 kernel: [  288.531134] 8021q: adding VLAN 0 to HW filter on device enP4p1s0f0
Apr 16 09:16:57 l82471p1 kernel: [  288.533512] bond0: Enslaving enP4p1s0f0 as a backup interface with a down link
Apr 16 09:16:57 l82471p1 kernel: [  288.557247] rename25: renamed from bond0.11
Apr 16 09:16:57 l82471p1 systemd-udevd[6941]: Could not generate persistent MAC address for virbr11: No such file or directory
Apr 16 09:16:57 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:16:57 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:16:57 l82471p1 kernel: [  288.644036] bond0: Adding slave enP5p9s0f1
Apr 16 09:16:57 l82471p1 systemd[1]: Started ifup for virbr11.
Apr 16 09:16:57 l82471p1 systemd[1]: Found device /sys/subsystem/net/devices/virbr11.
Apr 16 09:16:57 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:16:57 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:16:58 l82471p1 kernel: [  289.160280] bnx2x 0005:09:00.1 enP5p9s0f1: using MSI-X  IRQs: sp 398  fp[0] 400 ... fp[7] 407
Apr 16 09:16:58 l82471p1 kernel: [  289.339200] 8021q: adding VLAN 0 to HW filter on device enP5p9s0f1
Apr 16 09:16:58 l82471p1 sh[7154]: Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Apr 16 09:16:58 l82471p1 kernel: [  289.343452] bond0: Enslaving enP5p9s0f1 as a backup interface with a down link
Apr 16 09:16:58 l82471p1 sh[7154]: ifup: interface bond0 already configured
Apr 16 09:16:58 l82471p1 sh[7154]: ERROR: trying to add VLAN #11 to IF -:bond0:-  error: File exists
Apr 16 09:16:58 l82471p1 sh[7154]: interface bond0.11 does not exist!
Apr 16 09:16:58 l82471p1 sh[7154]: Waiting for virbr11 to get ready (MAXWAIT is 32 seconds).
Apr 16 09:16:58 l82471p1 systemd[1]: Started ifup for bond0.
Apr 16 09:16:58 l82471p1 sh[7307]: ifup: interface bond0 already configured
Apr 16 09:16:58 l82471p1 systemd[1]: Found device /sys/subsystem/net/devices/bond0.
Apr 16 09:16:58 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:16:58 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:16:58 l82471p1 ifup[6803]: /sbin/ifup: waiting for lock on /run/network/ifstate.virbr11
Apr 16 09:16:58 l82471p1 kernel: [  289.487149] bnx2x 0004:01:00.0 enP4p1s0f0: NIC Link is Up, 10000 Mbps full duplex, Flow control: ON - receive & transmit
Apr 16 09:16:58 l82471p1 kernel: [  289.550922] bond0: link status definitely up for interface enP4p1s0f0, 10000 Mbps full duplex
Apr 16 09:16:58 l82471p1 kernel: [  289.550929] bond0: Warning: No 802.3ad response from the link partner for any adapters in the bond
Apr 16 09:16:58 l82471p1 kernel: [  289.550937] bond0: first active interface up!
Apr 16 09:16:58 l82471p1 kernel: [  289.551041] IPv6: ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
Apr 16 09:16:58 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:16:58 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:16:58 l82471p1 ifup[6803]: Waiting for bond master bond1 to be ready
Apr 16 09:16:58 l82471p1 systemd-udevd[7162]: Could not generate persistent MAC address for bond1: No such file or directory
Apr 16 09:16:58 l82471p1 kernel: [  289.671356] bonding: bond1 is being created...
Apr 16 09:16:58 l82471p1 kernel: [  289.699739] bond1: Setting xmit hash policy to layer3+4 (1)
Apr 16 09:16:58 l82471p1 kernel: [  289.699869] bond1: Setting MII monitoring interval to 100
Apr 16 09:16:58 l82471p1 kernel: [  289.699974] bond1: Setting down delay to 0
Apr 16 09:16:58 l82471p1 kernel: [  289.700079] bond1: Setting up delay to 0
Apr 16 09:16:58 l82471p1 kernel: [  289.703839] bond1: Setting LACP rate to fast (1)
Apr 16 09:16:58 l82471p1 kernel: [  289.704507] IPv6: ADDRCONF(NETDEV_UP): bond1: link is not ready
Apr 16 09:16:58 l82471p1 kernel: [  289.704510] 8021q: adding VLAN 0 to HW filter on device bond1
Apr 16 09:16:58 l82471p1 kernel: [  289.776953] bond1: Adding slave enP4p1s0f1
Apr 16 09:16:59 l82471p1 kernel: [  290.276113] bnx2x 0004:01:00.1 enP4p1s0f1: using MSI-X  IRQs: sp 465  fp[0] 467 ... fp[7] 474
Apr 16 09:16:59 l82471p1 kernel: [  290.295155] bnx2x 0005:09:00.1 enP5p9s0f1: NIC Link is Up, 10000 Mbps full duplex, Flow control: ON - receive & transmit
Apr 16 09:16:59 l82471p1 kernel: [  290.459223] 8021q: adding VLAN 0 to HW filter on device enP4p1s0f1
Apr 16 09:16:59 l82471p1 kernel: [  290.461672] bond1: Enslaving enP4p1s0f1 as a backup interface with a down link
Apr 16 09:16:59 l82471p1 kernel: [  290.462947] bond0: link status definitely up for interface enP5p9s0f1, 10000 Mbps full duplex
Apr 16 09:16:59 l82471p1 kernel: [  290.495963] rename28: renamed from bond1.19
Apr 16 09:16:59 l82471p1 systemd-udevd[7328]: Could not generate persistent MAC address for virbr19: No such file or directory
Apr 16 09:16:59 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:16:59 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:16:59 l82471p1 kernel: [  290.581841] bond1: Adding slave enP5p9s0f0
Apr 16 09:16:59 l82471p1 systemd[1]: Started ifup for virbr19.
Apr 16 09:16:59 l82471p1 systemd[1]: Found device /sys/subsystem/net/devices/virbr19.
Apr 16 09:16:59 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:16:59 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:17:00 l82471p1 kernel: [  291.083925] bnx2x 0005:09:00.0 enP5p9s0f0: using MSI-X  IRQs: sp 388  fp[0] 390 ... fp[7] 397
Apr 16 09:17:00 l82471p1 kernel: [  291.263135] 8021q: adding VLAN 0 to HW filter on device enP5p9s0f0
Apr 16 09:17:00 l82471p1 sh[7765]: Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Apr 16 09:17:00 l82471p1 kernel: [  291.267297] bond1: Enslaving enP5p9s0f0 as a backup interface with a down link
Apr 16 09:17:00 l82471p1 sh[7765]: ifup: interface bond1 already configured
Apr 16 09:17:00 l82471p1 sh[7765]: ERROR: trying to add VLAN #19 to IF -:bond1:-  error: File exists
Apr 16 09:17:00 l82471p1 sh[7765]: interface bond1.19 does not exist!
Apr 16 09:17:00 l82471p1 sh[7765]: Waiting for virbr19 to get ready (MAXWAIT is 32 seconds).
Apr 16 09:17:00 l82471p1 systemd[1]: Started ifup for bond1.
Apr 16 09:17:00 l82471p1 sh[7902]: ifup: interface bond1 already configured
Apr 16 09:17:00 l82471p1 systemd[1]: Found device /sys/subsystem/net/devices/bond1.
Apr 16 09:17:00 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:17:00 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:17:00 l82471p1 ifup[6803]: /sbin/ifup: waiting for lock on /run/network/ifstate.virbr19
Apr 16 09:17:00 l82471p1 kernel: [  291.415191] bnx2x 0004:01:00.1 enP4p1s0f1: NIC Link is Up, 10000 Mbps full duplex, Flow control: ON - receive & transmit
Apr 16 09:17:00 l82471p1 kernel: [  291.502928] bond1: link status definitely up for interface enP4p1s0f1, 10000 Mbps full duplex
Apr 16 09:17:00 l82471p1 kernel: [  291.502935] bond1: Warning: No 802.3ad response from the link partner for any adapters in the bond
Apr 16 09:17:00 l82471p1 kernel: [  291.502943] bond1: first active interface up!
Apr 16 09:17:00 l82471p1 kernel: [  291.503050] IPv6: ADDRCONF(NETDEV_CHANGE): bond1: link becomes ready
Apr 16 09:17:00 l82471p1 systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 16 09:17:00 l82471p1 systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 16 09:17:00 l82471p1 systemd[1]: Started Raise network interfaces.
Apr 16 09:17:01 l82471p1 kernel: [  292.219151] bnx2x 0005:09:00.0 enP5p9s0f0: NIC Link is Up, 10000 Mbps full duplex, Flow control: ON - receive & transmit
Apr 16 09:17:01 l82471p1 kernel: [  292.302925] bond1: link status definitely up for interface enP5p9s0f0, 10000 Mbps full duplex
Apr 16 09:17:01 l82471p1 CRON[7997]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
root@l82471p1:~#
```



Still searching for missing link..... (certainly not me as I seem unable to build this correctly...)

Thanks

---

### Post by penguinpages2 on 2018-05-17
Back at this forum thread.   A few updates for those, like me who are still wallowing in how to make Ubunutu KVM NSPOF for larger enviornments where NSPOF is required.

Here is what I have so far:  Switch side keep simple: mode trunk  allow all vlans,  no untagged traffic so all open switch configurations can specify and bind tagging.

Each server has four 10Gb ports, two for vm and mgmt and two for block / data

root@l82471p1:~# cat /etc/network/interfaces
##########
source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


###### Bond0 for mgmt and VM traffic
#enP4p1s0f0 configuration sw26-10
auto enP4p1s0f0
iface enP4p1s0f0 inet manual
bond-master bond0


#enP5p9s0f1 configuration sw20-09
auto enP5p9s0f1
iface enP5p9s0f1 inet manual
bond-master bond0


auto bond0
iface bond0 inet manual
# bond0 uses standard balance-xor bonding protocol
bond-mode 2
bond-miimon 100
bond-slaves enP4p1s0f0 enP5p9s0f1


# VLAN 11 with mgmt IP bound and DGW
auto bond0.11
iface bond0.11 inet static
address 172.20.11.132
netmask 255.255.255.0
gateway 172.20.11.1
dns-nameservers 172.20.12.100
vlan-raw-device bond0


###### Bond for block and data


#enP4p1s0f1 configuration sw20-10
auto enP4p1s0f1
iface enP4p1s0f1 inet manual
bond-master bond1


#enP5p9s0f0 configuration sw26-09
auto enP5p9s0f0
iface enP5p9s0f0 inet manual
bond-master bond1


auto bond1
iface bond1 inet manual
# bond1 uses standard balance-xor LACP bonding protocol
bond-mode 2
bond-miimon 100
bond-slaves enP4p1s0f1 enP5p9s0f0


# VLAN 19 with mgmt IP bound
auto bond1.19
iface bond1.19 inet static
address 172.20.19.192
netmask 255.255.255.0
vlan-raw-device bond1
root@l82471p1:~#
################
Switch side.. Example is a 10Gb Brocade VDX switch... but the nice thing is ALL ports are same, and no fancy / brittle configuration of LACP aggregation.  BTW.. this is how VMWare, and HyperV do theirs also, so like me, flipping OS or such makes it supper easy. 
###
interface TenGigabitEthernet 20/0/9
 description l8247l1p1_enP5p9s0f1
 switchport
 switchport mode trunk
 switchport trunk allowed vlan all
 switchport trunk tag native-vlan
 no spanning-tree shutdown
 fabric isl enable
 fabric trunk enable
 storm-control ingress broadcast limit-percent 5 monitor
 storm-control ingress multicast limit-percent 5 monitor
 storm-control ingress unknown-unicast limit-percent 5 monitor
 fcoeport 027ATLIBMVSAN
 no shutdown
!
########
So now the story goes on...... follow docs to lay down Novalink for Openstack control....


Create IBM Novalink Repository for version.  [https://public.dhe.ibm.com/systems/virtualization/Novalink/readme/](https://public.dhe.ibm.com/systems/virtualization/Novalink/readme/)  1.0.0.9  seems to be latest
Bind the br-ex to bond0.11
[TABLE]
[TR]
[TD] 
administrator@l82472p1:~$ sudo vi /etc/apt/sources.list.d/pvm.list
sudo: unable to resolve host l82472p1: Connection timed out
[sudo] password for administrator:
[TABLE]
[TR]
[TD]deb [http://public.dhe.ibm.com/systems/virtualization/Novalink/debian](http://public.dhe.ibm.com/systems/virtualization/Novalink/debian) novalink_1.0.0.9 non-free
[/TD]
[/TR]
[/TABLE]

administrator@l82472p1:~$ sudo apt-get install openvswitch-switch
sudo: unable to resolve host l82472p1: Connection timed out
Reading package lists... Done
&#8230;
administrator@l82471p1:~$ sudo ovs-vsctl add-br br-ex
administrator@l82471p1:~$ sudo ovs-vsctl add-port br-ex bond0.11
[/TD]
[/TR]
[/TABLE]

 
&#8230;
 
well.. that went poorly&#8230;   took down ip stack..
 
[https://ask.openstack.org/en/question/67738/br-ex-configuration-on-ubuntu/](https://ask.openstack.org/en/question/67738/br-ex-configuration-on-ubuntu/) 
 
Testing&#8230;
[TABLE]
[TR]
[TD]root@l82471p1:~# ping 172.20.11.1
PING 172.20.11.1 (172.20.11.1) 56(84) bytes of data.
From 172.20.11.132 icmp_seq=1 Destination Host Unreachable
From 172.20.11.132 icmp_seq=2 Destination Host Unreachable
From 172.20.11.132 icmp_seq=3 Destination Host Unreachable
From 172.20.11.132 icmp_seq=4 Destination Host Unreachable
From 172.20.11.132 icmp_seq=5 Destination Host Unreachable
From 172.20.11.132 icmp_seq=6 Destination Host Unreachable
From 172.20.11.132 icmp_seq=7 Destination Host Unreachable
From 172.20.11.132 icmp_seq=8 Destination Host Unreachable
From 172.20.11.132 icmp_seq=9 Destination Host Unreachable
^C
--- 172.20.11.1 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9047ms
pipe 3
root@l82471p1:~# ifconfig br-ex promisc up
root@l82471p1:~# ifconfig bond0.11 172.20.11.200
root@l82471p1:~# ifconfig bond0.11 promisc
root@l82471p1:~# ifconfig bond0.11 0.0.0.0
root@l82471p1:~# ifconfig bond0.11 172.20.11.200 netmask 255.255.255.0
root@l82471p1:~# ovs-vsctl add-port br-ex bond0.11
ovs-vsctl: unix:/var/run/openvswitch/db.sock: database connection failed (No such file or directory)
root@l82471p1:~# ip route add default via 172.20.11.1
root@l82471p1:~#
root@l82471p1:~# ifconfig
bond0     Link encap:Ethernet  HWaddr 98:be:94:59:fe:11
          inet6 addr: fe80::9abe:94ff:fe59:fe11/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:86955 errors:0 dropped:5580 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15243529 (15.2 MB)  TX bytes:37452 (37.4 KB)


bond1     Link encap:Ethernet  HWaddr 98:be:94:59:fe:10
          inet6 addr: fe80::9abe:94ff:fe59:fe10/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:3306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:282876 (282.8 KB)  TX bytes:1392 (1.3 KB)


bond0.11  Link encap:Ethernet  HWaddr 98:be:94:59:fe:11
          inet addr:172.20.11.200  Bcast:172.20.11.255  Mask:255.255.255.0
          inet6 addr: fe80::9abe:94ff:fe59:fe11/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:15316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:897758 (897.7 KB)  TX bytes:31068 (31.0 KB)


bond1.19  Link encap:Ethernet  HWaddr 98:be:94:59:fe:10
          inet addr:172.20.19.192  Bcast:172.20.19.255  Mask:255.255.255.0
          inet6 addr: fe80::9abe:94ff:fe59:fe10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:210636 (210.6 KB)  TX bytes:648 (648.0 B)


br-ex     Link encap:Ethernet  HWaddr 98:be:94:59:fe:11
          inet6 addr: fe80::9abe:94ff:fe59:fe11/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:10539 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:0 (0.0 B)  TX bytes:648 (648.0 B)


enP4p1s0f0 Link encap:Ethernet  HWaddr 98:be:94:59:fe:11
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:43428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7583063 (7.5 MB)  TX bytes:1420 (1.4 KB)
          Interrupt:225 Memory:240000000000-2400007fffff


enP4p1s0f1 Link encap:Ethernet  HWaddr 98:be:94:59:fe:10
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:141438 (141.4 KB)  TX bytes:0 (0.0 B)
          Interrupt:226 Memory:240001000000-2400017fffff


enP5p9s0f0 Link encap:Ethernet  HWaddr 98:be:94:59:fe:10
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:141438 (141.4 KB)  TX bytes:1392 (1.3 KB)
          Interrupt:222 Memory:250100000000-2501007fffff


enP5p9s0f1 Link encap:Ethernet  HWaddr 98:be:94:59:fe:11
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:43527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7660466 (7.6 MB)  TX bytes:36032 (36.0 KB)
          Interrupt:223 Memory:250101000000-2501017fffff


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:56352 (56.3 KB)  TX bytes:56352 (56.3 KB)


virbr0    Link encap:Ethernet  HWaddr 52:54:00:1c:3f:fc
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


[/TD]
[/TR]
[/TABLE]

 

All IP traffic now has ceased...



I am trying to figure out.. what exactly that command did..  where it saved it.. and why a reboot does not fix it as it (like any other normal command for Linux, should require it to be added to the /etc/network/interfaces  file before it messes with the system state on reboot.

<scratches head>

Maybe someone can point me to a better manual or guide on how to do Ubuntu KVM NSPOF network configurations.....  As this process so far has been a bit painful.

---

### Post by penguinpages2 on 2018-05-19
Well thanks to a friend of mine.  Who, as always goes above and beyond to help others. ..  I have what I hope to be final posting for this thread:


His team has done a good job documenting the basic design of my goal.. for Ubuntu 16.  [http://www.redbooks.ibm.com/redpapers/pdfs/redp5455.pdf](http://www.redbooks.ibm.com/redpapers/pdfs/redp5455.pdf)  Page: 20.


 


1) Don't use bonds.. bonds are a PITA and not nessisary when you can get perks from use of OpenSwitch.
2) Physical switch side KISS and use "trunk allow vlan all"  sure.... all packets must be tagged.   all ports same.

My difference and what caught me was that I wanted all outbound tagged from the referance document.. Which I don't think is that unusual. 




Here is how you configure NSPOF Bridged KVM Openswitch with VLAN tagging.  One IP for mgmt on VLAN 11 the other for iSCSI / Object / etc.. on VLAN 19
###################
Copy URL from  &#8220;README.txt&#8221;  to /etc/apt/sources.list.d/ibm_novalink.list
 
Ex:
[ftp://public.dhe.ibm.com/systems/virtualization/Novalink/debian/README.txt](ftp://public.dhe.ibm.com/systems/virtualization/Novalink/debian/README.txt)  
[IMG]file:///C:/Users/JEREME~1/AppData/Local/Temp/msohtmlclip1/02/clip_image001.png[/IMG]Add it to a repository target file.
[TABLE]
[TR]
[TD]administrator@l82471p1:/etc $ sudo vi /etc/apt/sources.list.d/ibm_novalink.list
[TABLE]
[TR]
[TD]deb [http://public.dhe.ibm.com/systems/virtualization/Novalink/debian/](http://public.dhe.ibm.com/systems/virtualization/Novalink/debian/) novalink_1.0.0 non-free
[/TD]
[/TR]
[/TABLE]

administrator@l82472p1:/etc/network$ sudo apt get update
administrator@l82472p1:/etc/network$ sudo  apt-get install kvm-novalink
<snip>
update-alternatives: using /usr/bin/python2-oslo-config-generator to provide /usr/bin/oslo-config-generator (oslo-config-generator) in auto mode
Setting up python-oslo.log (3.2.0-2) ...
Setting up python-oslo.concurrency (3.7.1-0ubuntu1.1) ...
update-alternatives: using /usr/bin/python2-lockutils-wrapper to provide /usr/bin/lockutils-wrapper (lockutils-wrapper) in auto mode
Setting up pypowervm (1.1.14-180410-3805) ...
Setting up pvm-cli (1.0.0.9-180222-2851) ...
Installing bash completion script /etc/bash_completion.d/python-argcomplete.sh
Setting up kvm-novalink (1.0.0.9.1-180410-360) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
administrator@l82472p1:/etc/network$
 
[/TD]
[/TR]
[/TABLE]


 
For KVM we will use Open Switch.  Makes it much easier to manage
*Note: you should shut down all networking before hand as Ubuntu gets confused if interfaces are not in interfaces file.
[TABLE]
[TR]
[TD]administrator@l82471p1:~$ sudo apt-get install openvswitch-switch
administrator@l82471p1:~$ sudo apt-get install kvm-novalink
root@l8247l1p1:~# cp /etc/network/interfaces /etc/network/interfaces.backup
 
[TABLE]
[TR]
[TD]root@l8247l1p1:~# sudo vi /etc/network/interfaces
[/TD]
[TD]Switch side:  Ex Brocade VDX 6740 all ports the same&#8230;
[/TD]
[/TR]
[TR]
[TD]# The loopback network interface
auto lo
iface lo inet loopback
 
 
# The ovs bridge
auto br-ex
allow-ovs br-ex
iface br-ex inet manual
       ovs_type OVSBridge
       ovs_ports br_ex_bond mgmt
 
allow-br-ex br_ex_bond
iface br_ex_bond inet manual
       ovs_bridge br-ex
       ovs_type OVSBond
       ovs_bonds enP4p1s0f0 enP4p1s0f1 enP5p9s0f0 enP5p9s0f1
       ovs_options bond_mode=balance-slb other_config:bond-detect-mode=carrier
 
allow-br-ex mgmt
iface mgmt inet static
       ovs_bridge br-ex
       ovs_type OVSIntPort
       ovs_options tag=11
       ovs_extra set interface ${IFACE} external-ids:iface-id=$(hostname -s)
       address 172.20.11.133
       netmask 255.255.255.0
       gateway 172.20.11.1
       dns-nameservers 172.20.12.100 172.20.13.100
       dns-search ibm.aessatl.arrow.com
 
allow-br-ex storage
iface storage inet static
       ovs_bridge br-ex
       ovs_type OVSIntPort
       ovs_options tag=19
       ovs_extra set interface ${IFACE} external-ids:iface-id=$(hostname -s)
       address 172.20.19.193
       netmask 255.255.255.0
[/TD]
[TD]sw12(conf-if-te-20/0/9-12)# do sh run int ten 20/0/9
interface TenGigabitEthernet 20/0/9
 description l8247l1p1_enP5p9s0f1
 switchport
 switchport mode trunk
 switchport trunk allowed vlan all
 switchport trunk tag native-vlan
 no spanning-tree shutdown
 fabric isl enable
 fabric trunk enable
 storm-control ingress broadcast limit-percent 5 monitor
 storm-control ingress multicast limit-percent 5 monitor
 storm-control ingress unknown-unicast limit-percent 5 monitor
 fcoeport 027ATLIBMVSAN
 no shutdown
!
[/TD]
[/TR]
[/TABLE]

sudo systemctl restart networking.service
# Test
administrator@l82472p1:/etc/network$ ping 172.20.19.1 -I storage
PING 172.20.19.1 (172.20.19.1) from 172.20.19.193 storage: 56(84) bytes of data.
64 bytes from 172.20.19.1: icmp_seq=1 ttl=64 time=1.89 ms
64 bytes from 172.20.19.1: icmp_seq=2 ttl=64 time=0.298 ms
64 bytes from 172.20.19.1: icmp_seq=3 ttl=64 time=0.499 ms
^C
--- 172.20.19.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.298/0.897/1.894/0.709 ms
administrator@l82472p1:/etc/network$ ping 172.20.11.1 -I mgmt
PING 172.20.11.1 (172.20.11.1) from 172.20.11.133 mgmt: 56(84) bytes of data.
64 bytes from 172.20.11.1: icmp_seq=1 ttl=64 time=0.279 ms
64 bytes from 172.20.11.1: icmp_seq=2 ttl=64 time=0.274 ms
^C
--- 172.20.11.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.274/0.276/0.279/0.016 ms
administrator@l82472p1:/etc/network$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
172.20.11.1              ether   00:24:38:bf:b7:40   C                     mgmt
172.20.19.1              ether   00:24:38:bf:b7:40   C                     storage
administrator@l82472p1:/etc/network$
 
[/TD]
[/TR]
[/TABLE]

---

