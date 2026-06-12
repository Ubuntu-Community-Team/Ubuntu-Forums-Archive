---
title: "Allow connections to remote LAN using openVPN"
date: 2018-02-08
forum: Networking &amp; Wireless
---

### Post by ricardsantacreu on 2018-02-08
Hello,

this is my network Topoly:

[IMG]https://i.imgur.com/bMQvn7z.jpg[/IMG]

what I'm trying to do is that, all clients on LAN B can access to network 192.168.2.0/24 (LAN A), the following is the server.conf

server.conf

```
dev tun
proto tcp
port 992
ca /etc/openvpn/easy-rsa/pki/ca.crt
cert /etc/openvpn/easy-rsa/pki/issued/server_rYylZ14K3QW5FSGY.crt
key /etc/openvpn/easy-rsa/pki/private/server_rYylZ14K3QW5FSGY.key
dh /etc/openvpn/easy-rsa/pki/dh2048.pem
topology subnet
server 10.8.0.0 255.255.255.0
# server and remote endpoints
ifconfig 10.8.0.1 10.8.0.2
# Add route to Client routing table for the OpenVPN Server
push "route 10.8.0.1 255.255.255.255"
# Add route to Client routing table for the OPenVPN Subnet
push "route 10.8.0.0 255.255.255.0"
# your local subnet
push "route 192.168.2.0 255.255.255.0"
# Set your primary domain name server address for clients
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
# Override the Client default gateway by using 0.0.0.0/1 and
# 128.0.0.0/1 rather than 0.0.0.0/0. This has the benefit of
# overriding but not wiping out the original default gateway.
push "redirect-gateway def1"
client-to-client
keepalive 10 120
remote-cert-tls client
tls-version-min 1.2
tls-auth /etc/openvpn/easy-rsa/pki/ta.key 0
cipher AES-256-CBC
auth SHA256
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
crl-verify /etc/openvpn/crl.pem
status /var/log/openvpn-status.log 20
status-version 3
log /var/log/openvpn.log
verb 1
# Generated for use by PiVPN.io
```


I enabled ip forwarding on server side on /etc/sysctl.con

net.ipv4.ip_forward=1

and on LAN B I created manual routes to reach 192.168.2.0 using gateway 192.168.1.6, I don't know what is wrong on my configuration, the VPN establish with no problem at boot, boot other PCs from LAN B, can only reach 10.8.0.2 wich is tun0 on openvpn client.

Can anyone take a look?
Many thanks for your help

Best regards

---

### Post by TheFu on 2018-02-08
Probably need to see the routes on both routers and both servers to see they are sending traffic to each other.

Why use TCP for the openvpn protocol?  Is there a firewall preventing the use of UDP?

Where are the 10.x.x.x networks? Need to see those on the diagram.

Please use **code tags**  <Adv> (#) when posting config files and command output. Too hard to read otherwise.

---

### Post by ricardsantacreu on 2018-02-08
Hello,

sorry to not use code tag, I'll try to use on the following replies:

On routers there aren't any special routes, are ISP routers connectly directly to internet, so I can't add or delete routes on 192.168.2.1 and 192.168.1.1, for this reason I'm adding manualy a route on windows computer, there are only 2, so that's not a problem.

I can set up OpenSSH default UDP port, there is no problem.
I'll show the new diagram with 10.8.0.XXX/24, this network is used by openvpn on tun0 on openVPN server and on openVPN client.

I'll show the routes on server(OpenVPN)

Server routes

```
root@SDopenVPN:~# route -F
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    202    0        0 ens160
10.8.0.0        *               255.255.255.0   U     0      0        0 tun0
192.168.2.0     *               255.255.255.0   U     202    0        0 ens160
root@SDopenVPN:~#
```

From 192.168.1.6 I can reach both IPs 10.8.0.2 (localhost), 10.8.0.1 (server OpenVPN) and also all the network 192.168.2.0/24, but I want to use 192.168.1.6 as gateway for other computers on 192.168.1.0/24 network.

[IMG]https://i.imgur.com/0xBdY25.jpg[/IMG]

Thanks
Best regards

---

### Post by TheFu on 2018-02-08
If you want the VPNs to do all routing between the networks, then those devices have to be THE routers for all clients and the routing between them manually configured. Is .6 setup as a router and do all client machines point to it as their gateway for the traffic you want handled?

---

### Post by SeijiSensei on 2018-02-08
What if you use these routes?

On server in LAN A
```
sudo ip route add 192.168.1.0/24 via 10.8.0.2
```
and on the the server in LAN B
```
sudo ip route add 192.168.2.0/24 via 10.8.0.1
```

You have to configure the client machines to use 192.168.1.6 and 192.168.2.2 as their gateway routers, not the 192.168.1.1 and 2.1 routers.  Then all the traffic from the clients will flow into, e.g., 192.168.1.6 and be forwarded on either to the other end of the tunnel or to 192.168.1.1 for further processing.

---

### Post by ricardsantacreu on 2018-02-08
> **TheFu said:**
> If you want the VPNs to do all routing between the networks, then those devices have to be THE routers for all clients and the routing between them manually configured. Is .6 setup as a router and do all client machines point to it as their gateway for the traffic you want handled?

Hello,

what I want is to all clients from network 192.168.1.0/24 to reach 192.168.2.0/24 using gateway 192.168.1.6 (openVPN client with 10.8.0.2), the routing from windows clients is ok, I have added the following route:

add route 192.168.2.0 mask 255.255.255.0 192.168.1.6

It's more clear now? I want to use the openVPN tunnel to reach 192.168.2.0/24 network

Thanks
Best regards

---

