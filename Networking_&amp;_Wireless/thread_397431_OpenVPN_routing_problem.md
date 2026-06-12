---
title: "OpenVPN routing problem"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by espenfjo on 2007-03-30
Hi,
Im having a problem with some routes on my OpenVPN setup..
After connecting to the server from my client i see this in the server log:
> Mar 30 21:54:53 oxygen ovpn-local[24378]: oxygen.xxx.org/80.212.110.xxx:60307 MULTI: bad source address from client [192.168.1.102], packet dropped
And i cant reach anything but the server.


80.212.110.xxx is the IP of mye ADSL modem
oxygen.xxx.org is the openvpn server
192.168.1.102 is the client behind the ADSL modem, using NAT
This is my server config:
```

dev tun
ifconfig 10.0.0.1 10.0.0.2 // IP of the local tun device and its peer
dh dh2048.pem
ca ca.crt
cert server.crt
key server.key
proto udp
comp-lzo
port 1194
user nobody
group nobody
server 10.0.0.0 255.255.255.0
push "redirect-gateway"
client-to-client
push "dhcp-option DNS 10.0.0.1"
ifconfig-pool-persist ipp.txt
verb 4
push "route 192.168.1.0 255.255.255.0"
```

This is my client config
```

client
dev tun
proto udp
remote oxygen.tihlde.org 1194
resolv-retry infinite
nobind
persist-key
persist-tun
mute-replay-warnings
ca ca.crt
cert helium.crt
key helium.key
comp-lzo
verb 3
```

This is my routing table on the client:
158.38.xx.xx is the OpenVPN server
> 
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
158.38.xx.xx    192.168.1.1     255.255.255.255 UGH   0      0        0 eth1
10.0.0.0        10.0.0.5        255.255.255.0   UG    0      0        0 tun0
192.168.1.0     10.0.0.5        255.255.255.0   UG    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.0.0.5        0.0.0.0         UG    0      0        0 tun0


This is the routing table on the server:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
158.38.xx.0     0.0.0.0         255.255.255.192 U     0      0        0 eth0
10.0.0.0        10.0.0.2        255.255.255.0   UG    0      0        0 tun0
0.0.0.0         158.38.xx.1     0.0.0.0         UG    0      0        0 eth0


---

### Post by espenfjo on 2007-03-31
Ok, i managed to fix this somehow, dunno really what i did to make it work, but now i have another problem :P
I need to run it in bridged modus since i need multicast on the client, and that is only available on the server.

My server config now look like this, changed from dev tun to dev tap in client config, only change there.
```

dev tap0
;ifconfig 10.0.0.1 255.255.255.0 // IP of the local tun device and its peer
dh dh2048.pem
ca ca.crt
cert server.crt
key server.key
proto udp
comp-lzo
port 1194
user nobody
group nobody
server-bridge 10.0.0.1 255.255.255.0 10.0.0.50 10.0.0.100
;server 10.0.0.0 255.255.255.0
push "redirect-gateway"
client-to-client
ifconfig-pool-persist ipp.txt
verb 4
;client-config-dir ccd
;route 192.168.1.0 255.255.255.0
float
ping 10
ping-restart 120
status openvpn-status.log

```

My problem now is that i cant reach anything with this setup, i have ofcourse enabled the bridge with the bridge-start.sh script, and i think that should be ok.
server gets the ip 10.0.0.1, and client 10.0.0.50
ping 10.0.0.1 on the client gives no respons, same the other way round.

This is the routing table on the client
> 
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
158.38.xx.xx    192.168.1.1     255.255.255.255 UGH   0      v eth10        0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1vv
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 tap0


---

### Post by arcticblue on 2007-12-21
<sigh>  So many good questions go unanswered...

I am having this exact same problem and ran across this in a Google search.  If anyone has any suggestions, it would be greatly appreciated.

---

### Post by lonetree on 2008-01-15
Same here. I got my openvpn server working, but all my client can only get till the server and nothing else.

---

