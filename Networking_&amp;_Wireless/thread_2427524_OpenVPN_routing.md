---
title: "OpenVPN routing"
date: 2019-09-23
forum: Networking &amp; Wireless
---

### Post by dhorth on 2019-09-23
First off a disclaimer, I'm a windows software developer, not a linux guy or a network guy...

I've been struggling with OpenVPN now for a few days, I'm happy to post all the config files, but in general terms I have setup OpenVPN on an Ubuntu 19.04 server.  My goal is to allow remote machines full access to a remote network I have hosted on an ESXi server, all the clients are Windows 10, and the remote network is pretty much a mix.

My remote network IP is 10.10.0.0/24
additional server on remote network 10.10.0.200
OpenVPN is setup as 10.8.0.0

I have 2 nics in vpn machine
   ens36-> internet facing
   ens160 -> internal network (10.10.0.0/24)

With my current configuration the following is happening
client connects to VPN gets assigned IP 10.8.0.2
client 
  pings 10.8.0.2 (itself)
  pings 10.8.0.1 (tun0 adapter on server)
  pings 10.10.0.254 (ens160 adapter on server)
client can NOT ping 10.10.0.200

Server can ping 10.10.0.200 (add. server)
Server can ping 10.8.0.200 (client)

tcpdump on the server shows the request coming in and getting routed to 10.10.0.200
15:26:15.205220 IP 10.8.0.2 > 10.10.0.200: ICMP echo request, id 1, seq 1113, length 40


tcpdump on 10.10.0.200 (add server) shows the request coming in from the client but no response
15:24:01.352562 IP 10.8.0.2 > 10.10.0.200 ICMP echo request, id 1, seq 1110, length 40

I know I got some kind of routing issue, but I dont know how to solve it, remember I'm a SW guy

Please help, 

Here is my server.conf
```
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
dh dh.pem
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist /var/log/openvpn/ipp.txt
push "route 10.10.0.0 255.255.255.0"
push "route 10.8.0.0 255.255.255.0"
keepalive 10 120
tls-auth ta.key 0 # This file is secret
cipher AES-256-CBC
auth SHA256
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log         /var/log/openvpn/openvpn.log
explicit-exit-notify 1



```


ip a
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:12:72:89 brd ff:ff:ff:ff:ff:ff
    inet 10.10.0.254/24 brd 10.10.0.255 scope global ens160
       valid_lft forever preferred_lft forever
    inet6 fe80::20c:29ff:fe12:7289/64 scope link
       valid_lft forever preferred_lft forever
3: ens36: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
*********************
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none
    inet 10.8.0.1/24 brd 10.8.0.255 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::e3b1:cd95:be45:522a/64 scope link stable-privacy
       valid_lft forever preferred_lft forever

```

---

### Post by SeijiSensei on 2019-09-23
Could be a couple of things. 

First, did you enable packet forwarding on the machine acting as the OpenVPN server? You need to remove the hash mark from the line
```
net.ipv4.ip_forward=1
```
in the file /etc/sysctl.conf.  Then run "sudo sysctl -p".  Looks like you did this already.

You probably also need a route on the server at 10.10.0.200 like this:
```
sudo ip route add 10.0.8.0/24 via 10.10.0.254
```
Unless 10.10.0.254 is the default gateway for 10.10.0.200 it will send the packets for machines on the 10.0.8.0/24 network to that gateway which won't know what to with them.

Alternatively you can add a static route to the router that serves the 10.10.0.0/24 network that directs traffic for 10.0.8.0/24 to 10.10.0.254. That's probably a better global solution.  I have a machine that connects to some servers I maintain in the cloud via OpenVPN.  I added a route to the router for my local LAN that sends packets for the remote network to the machine with the OpenVPN tunnel.  All my machines can see the cloud servers.

---

### Post by dhorth on 2019-09-23
Found it, thank you.  Turns out in all my messing around I forgot I had changed the gateway address on the .200 server. putting it back to .254 solved the problem

---

