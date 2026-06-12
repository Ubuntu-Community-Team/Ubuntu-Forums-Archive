---
title: "LXD container + VPN + UFW killswitch"
date: 2023-05-21
forum: Networking &amp; Wireless
---

### Post by kinu on 2023-05-21
Hello! I'm not sure if this is the place to ask. If not, please excuse me and tell where to post.

So I've just begun using containers and trying to set a VPN gateway in one container to other containers. By know I've found two problems.

I've been searching and reading, and this is what I've done:

Created an Ubuntu LXD container (and a second one that is going to be the "client"), fixed ip for both, followed the guide in [https://ubuntu.com/server/docs/service-openvpn](https://ubuntu.com/server/docs/service-openvpn) doing this
```

apt update
apt upgrade
apt install openvpn 
apt install wget unrar unzip nano curl

wget https://ivacy.s3.amazonaws.com/support/OpenVPN-Configs-with-certificate.rar

unrar x OpenVPN-Configs-with-certificate.rar

cp vpntosingapore.ovpn /etc/openvpn/client.conf
```

the find the ip for my remote in **client.conf**, ping myremotename

then put ```
auth-user-pass userpass.txt
``` in client.conf and started the vpn client service

```

systemctl start openvpn@client
```

and my container is connected to my provider's VPN node in Singapore.

**_Set kill switch_**

```
apt install ufw

ufw disable
``` 

and then follow this [https://www.comparitech.com/blog/vpn-privacy/how-to-make-a-vpn-kill-switch-in-linux-with-ufw/](https://www.comparitech.com/blog/vpn-privacy/how-to-make-a-vpn-kill-switch-in-linux-with-ufw/) and/or this [https://askubuntu.com/questions/1148172/share-a-vpn-connection-over-ethernet](https://askubuntu.com/questions/1148172/share-a-vpn-connection-over-ethernet)

Make these changes in** /etc/sysctl.conf**
```

#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
#enable packet forwarding
net.ipv4.ip_forward=1
```

and this in **/etc/default/ufw**

```
IPV6=no
```

to disable ip6.

I did
```

sudo ufw allow in to 192.168.1.0/24
sudo ufw allow out to 192.168.1.0/24
```

to allow LAN (LXD lxdbr0 traffic)

then to block all traffic except LAN and tun0 (my VPN interface)

```
sudo ufw default deny incoming
sudo ufw default deny outgoing
sudo ufw allow out on tun0 from any to any
```

then 

```
sudo ufw allow out to ipofsingaporenode/24 port 53 proto udp
```

to allow OpenVPN to the nodo I want.

An it works! If I stop the VPN I can't reach the internet. Kill switch is set.

**_The route part_**

Ok. Now I want to route others containers using this one as a gateway.

Well, I edited **/etc/ufw/before.rules **and added NAT table rules, like this

```
*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE   
COMMIT
```

Then in the other container, set this as the gateway. Edited** /etc/netplan/mynetplan.yml**


```
network:
  version: 2
  ethernets:
  eth0:
    dhcp4: false
    addresses: [192.168.1.3/24] 
    routes:
      - to: default
        via: 192.168.1.2 #this is my openvpn client container
    nameservers:
      addresses: [1.1.1.1,1.0.0.1]
```

then ```
netplan apply
``` and then

ping 1.1.1.1, and it works too! traceroute shows me that I'm getting out through the openvpn container.

And then my first problem:_ there is no name resolution from this second container_. It is a clean, new one, the only thing I've touched is netplan file. What am I doing wrong? Because name resolution works from openvpn-client container, and of course it has name resolution if I route through 192.168.1.1, my lxdbr0 gateway.

_The second problem is port forwarding_. I want port 80 in the second container (installed a web server to test) to be accessed from the openvpn-client, so I incorporate this rules to **/etc/ufw/before.rules**
```

:POSTROUTING ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.168.1.3:80
-A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE   
COMMIT
``` 192.168.1.3 is the ip of my "second" container.

 in *nat rules in my** /etc/ufw/before.rules**. But I can't reach my server using [http://myovpncontainerip](http://myovpncontainerip). But I can reach it in [http://mysecondcontainerip](http://mysecondcontainerip), so it is working. What is wrong with my rule?

---

### Post by TheFu on 2023-05-21
For VPNs and firewall stuff, use a full virtual machine, not a container.  There are security reasons why this needs to be done this way.

BTW, to disable IPv6, the only way that works anymore is a grub parameter.  Thank the systemd guys.  The /etc/sysctl.conf settings haven't worked for years now, though setting them may still be necessary, it isn't enough to actually disable IPv6 like it was before.

---

### Post by kinu on 2023-05-22
> **TheFu said:**
> For VPNs and firewall stuff, use a full virtual machine, not a container.  There are security reasons why this needs to be done this way.
Ok. Done. Same problems arise.
> BTW, to disable IPv6, the only way that works anymore is a grub parameter.  Thank the systemd guys.  The /etc/sysctl.conf settings haven't worked for years now, though setting them may still be necessary, it isn't enough to actually disable IPv6 like it was before.
Yes, I have seen it, but containers do not have grub, you know. Now in the VM I can fix it. 

I have fixed the not-name-resolution setting up a dnsmasq server in my openvpn client instance, port 5353, and pointing my second container to it using systemd-resolve configuration.

But the problem forwarding ports from the openvpn-client instance to the "second" container still remains. Any idea?

---

