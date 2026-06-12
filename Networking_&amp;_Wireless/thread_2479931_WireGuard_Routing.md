---
title: "WireGuard Routing"
date: 2022-10-13
forum: Networking &amp; Wireless
---

### Post by rbravo1 on 2022-10-13
Hello Community!

I have installed WireGuard on Ubuntu 20 and am having trouble configuring the server to allow traffic out of a secondary network interface. Here is all of the configuration that I have so far:

# /etc/sysctl.conf
net.ipv4.ip_forward=1

# /etc/netplan/00-installer-config.yaml
network:
    version: 2
    renderer: networkd
    ethernets:
        enp3s0:
            dhcp4: yes
        enp5s0:
            addresses:
                - XXX.142.30.142/29
            nameservers:
                addresses: [64.71.255.196, 64.71.255.197]
            routes:
                - to: default
                  via: XXX.142.30.137

# /etc/wireguard/wg0.conf
[Interface]
Address = 10.0.0.1/24
ListenPort = 41194
SaveConfig = true
DNS = 64.71.255.196
PrivateKey = <key>
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -t nat -A POSTROUTING -o enp5s0 -j MASQUERADE
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -t nat -D POSTROUTING -o enp5s0 -j MASQUERADE

[Peer]
PublicKey = <Key>
AllowedIPs = 10.0.0.2/32

# ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:23:7d:65:2d:72 brd ff:ff:ff:ff:ff:ff
    inet 10.20.50.146/24 metric 100 brd 10.20.50.255 scope global dynamic enp3s0
       valid_lft 49533sec preferred_lft 49533sec
    inet6 fe80::223:7dff:fe65:2d72/64 scope link
       valid_lft forever preferred_lft forever
3: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:23:7d:65:2d:70 brd ff:ff:ff:ff:ff:ff
    inet XXX.142.30.142/29 brd 72.142.30.143 scope global enp5s0
       valid_lft forever preferred_lft forever
    inet6 fe80::223:7dff:fe65:2d70/64 scope link
       valid_lft forever preferred_lft forever
5: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:0f:98:3a:66 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
101: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.0.0.1/24 scope global wg0
       valid_lft forever preferred_lft forever
102: cali6acdeba6410@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1440 qdisc noqueue state UP group default
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-c710d1a9-b24e-ec5c-cad0-fa4199130a78
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link
       valid_lft forever preferred_lft forever
105: vxlan.calico: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1370 qdisc noqueue state UNKNOWN group default
    link/ether 66:23:28:db:6a:3f brd ff:ff:ff:ff:ff:ff
    inet 10.1.62.64/32 scope global vxlan.calico
       valid_lft forever preferred_lft forever
    inet6 fe80::6423:28ff:fedb:6a3f/64 scope link
       valid_lft forever preferred_lft forever

# ufw status
Status: active

To                         Action      From
--                         ------      ----
41194/udp                  ALLOW       Anywhere
Anywhere on vxlan.calico   ALLOW       Anywhere
Anywhere on cali+          ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
41194/udp (v6)             ALLOW       Anywhere (v6)
Anywhere (v6) on vxlan.calico ALLOW       Anywhere (v6)
Anywhere (v6) on cali+     ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)

Anywhere                   ALLOW OUT   Anywhere on vxlan.calico
Anywhere                   ALLOW OUT   Anywhere on cali+
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on vxlan.calico
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on cali+

Client Config:

[Interface]
PrivateKey = <Key>
Address = 10.0.0.2/24
DNS = 64.71.255.196

[Peer]
PublicKey = <Key>
AllowedIPs = 0.0.0.0/0
Endpoint = XXX.142.30.142:41194

From what I have read, I think I am missing something in the PostUp/PostDown to allow access to the network on the enp3s0 interface.

The interfaces 5, 102 and 105 were automatically created when I set up the Ubuntu server, I don't think these are affecting anything.

Any help that can be given would be really appreciated as I have hit a wall on this. Thank you!

---

### Post by TheFu on 2022-10-13
netplan YAML files are indentation sensitive.  Edit the post above to use proper code-tags, as supported by this forum software. Without that edit, nobody can help.   My signature has a link to a code-tag how-to, if you need it.

Around here, we really like, and sometimes need, code tags for anything shown in a terminal.  Config files, commands, and command output are usually it.  It is just too hard to read otherwise.  We deal with terminal sessions daily, constantly, so I actually prefer the mono-space fonts used in terminals.  It makes it easier for us to see exactly what we need to see, exactly where we expect it in the output.  

Please help us to help you.

---

