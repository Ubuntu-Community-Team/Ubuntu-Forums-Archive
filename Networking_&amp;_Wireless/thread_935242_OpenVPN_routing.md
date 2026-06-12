---
title: "OpenVPN routing"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by dbyrne on 2008-10-01
... is driving me nuts for several weeks now !

My home network is 192.168.0.0/24, OpenVPN server 192.168.0.111, OpenVPN network 192.168.64.0/24.

I've set it up as a routed network. Connection works fine, I can putty in from an XP client with no problems. 

Server config:

```
dev tun
proto udp
ca ca.crt
key server.key
dh dh1024.pem
server 192.168.64.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "dhcp-option DNS 192.168.0.111"

```


When the VPN is up, I can not ping 192.168.0.111 or 192.168.64.5
I can ping 192.168.64.1.

If I add the line:

```
push "route 192.168.0.0 255.255.255.0"
```

to the server config, I get an error in the client log:

```
RESOLVE: Cannot resolve host address: 192.168.0.0: [HOST_NOT_FOUND] The specified host is unknown.
```

and I can't see the server on the 192.168.0.111 address (ping it, access the Samba shares on it etc.). However if on the XP machine I run the command

```
route add 192.168.0.0 mask 255.255.255.0 192.168.64.5
```

then I can both ping the server on 192.168.0.111, and see the Samba shares on it.

Any ideas how I can get this route to come up automatically ?

I also think the client machine looks odd when the VPN is up and working:

C:\> ipconfig /all
...
Ethernet adapter MyTap:
     ...
     IP Address: 192.168.64.6               Looks OK
     Subnet mask: 255.255.255.252           Looks odd
     Default Gateway: 192.168.0.0           Looks odd
     DHCP Server: 192.168.64.5              Looks odd
     DNS Servers: 192.168.0.111             Looks OK
     ...

---

### Post by kevdog on 2008-10-13
Here is what I did since I was having the same problem

Removed the push statements from the server config (Just left the server statements)

In the client file, I just placed a line that stated:
redirect-gateway def1

Then everything seemed to work! Hopefully that will work for you!

---

