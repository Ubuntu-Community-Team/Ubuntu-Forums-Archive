---
title: "Static IP set still get another IP from DHCP server."
date: 2023-07-06
forum: Networking &amp; Wireless
---

### Post by xavierlinw2 on 2023-07-06
I'm on Ubuntu 22.04.2 LTS and **NetworkManager **is installed.
The computer is connected to a LAN where I work. This work place has DHCP, which I don't have control to.

I edited the file of /etc/network/interfaces on the computer as following:

auto br0
iface br0 inet static
        address [COLOR=#ff8c00]10.11.1.113[/COLOR]
        netmask 255.255.255.0
        gateway 10.11.1.1
        broadcast 10.11.1.255
        dns-nameservers 8.8.8.8 168.95.1.1

But when I do #** ip a** 
it shows..

br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 96:ab:7b:c8:fa:ec brd ff:ff:ff:ff:ff:ff
    inet [COLOR=#ff8c00]10.11.1.113[/COLOR]/24 brd 10.11.1.255 scope global br0
       valid_lft forever preferred_lft forever
    inet [COLOR=#0000ff]10.11.1.112[/COLOR]/24 brd 10.11.1.255 scope global secondary dynamic noprefixroute br0
       valid_lft 286sec preferred_lft 286sec
    inet6 fe80::edca:5cc8:b735:25b9/64 scope link noprefixroute
       valid_lft forever preferred_lft forever

It got the static IP [COLOR=#FF8C00]10.11.1.113 [/COLOR]as my setting, but also got another IP [COLOR=#0000ff]10.11.1.112[/COLOR] from the DHCP server.
I don't want the computer to get another IP from the DHCP server, in this case [COLOR=#0000FF]10.11.1.112, [/COLOR]even after rebooting.

How do I fix this?



Some info on br0 if needed. 

# **nmcli conn show**
NAME                UUID                                  TYPE      DEVICE
bridge-br0          f3d19268-2ad5-4e1a-a986-94e132842cf4  bridge    br0
bridge-slave-eth0   3729442d-bccf-4ca8-ac32-1e8c1544e6e9  ethernet  eth0
bridge-slave-eth4   2f24a76c-5f20-416f-b7f4-25a94bca813f  ethernet  --
Wired connection 1  2849a7f2-748b-3a29-b2d0-3d960628f886  ethernet  --
Wired connection 2  894428d1-d30a-3692-8512-e80165511e80  ethernet  --
Wired connection 3  3b83c1a0-eef3-32b2-9397-c1fac6d10c97  ethernet  --


# **nmcli dev status**
DEVICE  TYPE      STATE        CONNECTION
br0     bridge    connected    bridge-br0
eth0    ethernet  connected    bridge-slave-eth0
eth1    ethernet  unavailable  --
eth2    ethernet  unavailable  --
eth3    ethernet  unavailable  --
eth4    ethernet  unavailable  --
lo      loopback  unmanaged    --

---

### Post by TheFu on 2023-07-06
I don't think network-manager can handle bridges.

/etc/network/interfaces was deprecated in 2019.  Netplan is how server network configurations are handled since 2018. [https://netplan.io/](https://netplan.io/)
Bridges have to be tied to a specific ethernet device. The settings in the posted interface file don't do that.

BTW, you cannot just pick an IP address randomly.  Get the correct IP from the network admins who manage the network. Choosing an IP in the DHCP range is a failure, as you've learned.

---

