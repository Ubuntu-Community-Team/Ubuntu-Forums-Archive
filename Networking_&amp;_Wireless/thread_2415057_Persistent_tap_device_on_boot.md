---
title: "Persistent tap device on boot"
date: 2019-03-19
forum: Networking &amp; Wireless
---

### Post by kaz-kanso on 2019-03-19
Hello,

I have been trying to setup a virtual machine running Ubuntu 18.04 (on AWS) to automatically create a tap device and configure it with L3 address. The main reason behind wanting to do this is a light-weight VPN so that I can use of "ssh -w ..." to tunnel subnets between my local machine and the remote machine without needing to setup a full VPN.

I am able to set this up manually with out any issues by entering the following commands:
```

tunctl -u ubuntu -t tap0
ip addr add 10.1.0.2/30 dev tap0
ip link set dev tap0 up
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sysctl net.ipv4.ip_forward=1
sed -i 's/#PermitTunnel no/PermitTunnel yes/' /etc/ssh/sshd_config

```

However, I have been having a problem making line 2 above persistent. While I first tried netplan, it did not appear to work (I did not see any errors, but it did not apply the config on boot or "netplan --debug apply"). So I investigated using networkd. See config files below:

Config files are as follows:
```

ubuntu@xxx:~$ cat /etc/systemd/network/tap0.netdev  
[NetDev]
Name=tap0
Kind=tap
[Tap]
User=ubuntu


ubuntu@xxx:~$ cat /etc/systemd/network/50-tap0.network  
[Match]
Name=tap0


[Link]
MACAddress=00:11:11:11:11:11


[Network]
Address=10.0.0.2/24

```

On boot, I was expecting device tap0 to be created with layer 2 and 3 addresses as defined above. Alas, only layer 2 address is applied. That is,

```

ubuntu@ip-172-31-21-213:~$ ip addr show dev tap0
3: tap0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:11:11:11:11:11 brd ff:ff:ff:ff:ff:ff

```

From reading the man pages for systemd.netdev and systemd.network I dont see anything obvious missing. Also, extracting the debug log file from networkd below I dont see any errors or warning that might be relevant, see below. Can anyone give me a suggestion on what I am not doing correctly?

```

[FONT=monospace][COLOR=#000000]-- Logs begin at Tue 2019-03-19 09:55:32 UTC, end at Tue 2019-03-19 12:19:08 UTC. --[/COLOR]
Mar 19 12:14:57 ip-172-31-21-213 systemd[1]: Starting Network Service...
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Bus n/a: changing state UNSET &#8594; OPENING
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Added inotify watch for /run on bus n/a: 2
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Added inotify watch for /run/dbus on bus n/a: -1
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Bus n/a: changing state OPENING &#8594; WATCH_BIND
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Failed to open configuration file '/etc/systemd/networkd.conf': No such file or directory
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: timestamp of '/etc/systemd/network' changed
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: timestamp of '/run/systemd/network' changed
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /etc/systemd/network/50-tap0.network, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /run/systemd/network/10-netplan-eth0.network, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /run/systemd/network/10-netplan-eth0.link, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /lib/systemd/network/80-container-ve.network, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /lib/systemd/network/99-default.link, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /lib/systemd/network/80-container-host0.network, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /lib/systemd/network/80-container-vz.network, because it's not a regular file with suffix .netdev.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: loaded tap
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Created
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /etc/systemd/network/tap0.netdev, because it's not a regular file with suffix .network.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /run/systemd/network/10-netplan-eth0.link, because it's not a regular file with suffix .network.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Ignoring /lib/systemd/network/99-default.link, because it's not a regular file with suffix .network.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Flags change: +MULTICAST +BROADCAST
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Link 3 added
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: udev initialized link
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: netdev has index 3
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Saved original MTU: 1500
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Flags change: +MULTICAST +BROADCAST
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Link 2 added
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: udev initialized link
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Saved original MTU: 1500
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Flags change: +LOOPBACK +UP +LOWER_UP +RUNNING
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Link 1 added
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: udev initialized link
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Saved original MTU: 0
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Adding address: ::1/128 (valid forever)
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Adding address: 127.0.0.1/8 (valid forever)
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: rtnl: received address with invalid family 129, ignoring
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Enumeration completed
Mar 19 12:14:57 ip-172-31-21-213 systemd[1]: Started Network Service.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Flags change: +UP +LOWER_UP +RUNNING
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Gained carrier
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Adding address: 172.31.21.213/20 (valid forever)
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Flags change: -UP -LOWER_UP -RUNNING
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Lost carrier
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Removing address: 172.31.21.213/20 (valid forever)
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Link state is up-to-date
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: found matching network '/etc/systemd/network/50-tap0.network'
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Link is not managed by us
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Link is not managed by us
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Bringing link up
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: IPv6 successfully enabled
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Link state is up-to-date
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: found matching network '/run/systemd/network/10-netplan-eth0.network'
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Link does not request DHCPv6 prefix delegation
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Link is not managed by us
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Bringing link up
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: IPv6 successfully enabled
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Link state is up-to-date
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Virtualization Xen found in DMI (/sys/class/dmi/id/sys_vendor)
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Virtualization XEN, found /sys/hypervisor/properties/features with value 00000705, XENFEAT_dom0 (indicating the 'hardware domain') is not set.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Found VM virtualization xen
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: lo: Unmanaged
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: MAC address: 00:11:11:11:11:11
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Flags change: +UP
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: LLDP: Started LLDP client
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: tap0: Started LLDP.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Flags change: +UP +LOWER_UP +RUNNING
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: LLDP: Started LLDP client
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Started LLDP.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Gained carrier
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Acquiring DHCPv4 lease
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): STARTED on ifindex 2
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): DISCOVER
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): OFFER
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): REQUEST (requesting)
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): ACK
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): lease expires in 59min 58s
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): T2 expires in 52min 27s
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: DHCP CLIENT (0x95a68647): T1 expires in 29min 59s
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: DHCPv4 address 172.31.21.213/20 via 172.31.16.1
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Setting MTU: 9001
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Setting transient hostname: 'ip-172-31-21-213'
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: Not connected to system bus, not setting hostname.
Mar 19 12:14:57 ip-172-31-21-213 systemd-networkd[598]: eth0: Updating address: 172.31.21.213/20 (valid for 1h)
[/FONT]
```

---

### Post by kaz-kanso on 2019-03-19
Solved the problem, posting here incase its of use to anyone.

The network file needed some additional directives to support the nominal state of no carrier on tap0. The following is a working config that configures layer 3 address:
```

[Match]
Name=tap0


[Link]
RequiredForOnline=no


[Network]
ConfigureWithoutCarrier=true
Address=10.0.0.2/30
IPForward=ipv4
IPMasquerade=yes

```

It also has additional directives for configuring iptables. The important ones are RequiredForOnline and ConfigureWithoutCarrier.

---

