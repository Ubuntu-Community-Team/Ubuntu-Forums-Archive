---
title: "Huge Problems with iFemslave LACP"
date: 2019-01-02
forum: Networking &amp; Wireless
---

### Post by jbamford92 on 2019-01-02
Hi folks,

Im having huge issues with ifenslave on my Workstation when using a Bond0 in LACP. I can access the the whole network but when it comes to the Internet i have nothing but DNS issues. Yet Windows is fine so i know its not the config it is something to do with Ubuntu. It takes at least 10 to 15 boots just to get internet and its annoying i either have to keep editing the /etc/network/interfaces or run update-grub then reboot at least 10 to 15 times and only recently im having this problem. Would anyone have any ideas?

Here is what i have in my /etc/network/interfaces.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0
iface eth0 inet manual
bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096


# Second NIC
auto eth1
iface eth1 inet manual
        bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096


# Virtual NIC
auto bond0
iface bond0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.254
        dns-nameservers 192.168.1.17


# bond0 uses standard IEEE 802.3ad LACP bonding protocol
    bond-mode 4
    bond-miimon 100
    bond-lacp-rate fast
    bond-slaves eth0 eth1
    pre-up /sbin/ip link set dev $IFACE mtu 1500
    pre-up /sbin/ip link set dev $IFACE address 00:1b:7
    bond-downdelay 0
    bond-updelay 0
    bond-xmit_hash_policy 1

Thanks.

---

### Post by jbamford92 on 2019-01-02
> **jbamford92 said:**
> Hi folks,

Im having huge issues with ifenslave on my Workstation when using a Bond0 in LACP. I can access the the whole network but when it comes to the Internet i have nothing but DNS issues. Yet Windows is fine so i know its not the config it is something to do with Ubuntu. It takes at least 10 to 15 boots just to get internet and its annoying i either have to keep editing the /etc/network/interfaces or run update-grub then reboot at least 10 to 15 times and only recently im having this problem. Would anyone have any ideas?

Here is what i have in my /etc/network/interfaces.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0
iface eth0 inet manual
bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096


# Second NIC
auto eth1
iface eth1 inet manual
        bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096


# Virtual NIC
auto bond0
iface bond0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.254
        dns-nameservers 192.168.1.17


# bond0 uses standard IEEE 802.3ad LACP bonding protocol
    bond-mode 4
    bond-miimon 100
    bond-lacp-rate fast
    bond-slaves eth0 eth1
    pre-up /sbin/ip link set dev $IFACE mtu 1500
    pre-up /sbin/ip link set dev $IFACE address 00:1b:
    bond-downdelay 0
    bond-updelay 0
    bond-xmit_hash_policy 1

Thanks.


Update,

I disabled dnsmasq and seemed to of solved the problem. rebooted about 4 times and get DNS. 

Will update if any more problems.

Thank you.

---

