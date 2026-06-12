---
title: "OpenVPN bridged mode, getting into the 'local' network works. Internet access doesnt"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Lieter on 2008-11-26
Well like the title says:

I followed this guide to get everything up and running: [http://vickeryj.freeshell.org/notes/open_vpn_howto.htm](http://vickeryj.freeshell.org/notes/open_vpn_howto.htm)
I am able to initiate the VPN to my home network and i can ping all other devices there. However on the client side I cannot reach the internet when the VPN is online, disconnecting the VPN will give internet access back. I assume its a route thing. These are the routes on the client without VPN:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
145.92.12.0     *               255.255.252.0   U     2      0        0 wlan0
default         254.015.092.145 0.0.0.0         UG    0      0        0 wlan0

```

These are my routes with the VPN enabled on the client:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[MY HOME IP]  145.92.15.254   255.255.255.255 UGH   0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     0      0        0 tap0
145.92.12.0     *               255.255.252.0   U     2      0        0 wlan0
default         *               0.0.0.0         U     0      0        0 tap0

```

i think the fault lies in the default rule going through tap0 instead of wlan0.

The server config is as follows:
```

port 1194
proto udp
dev tap0
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key
dh /etc/openvpn/keys/dh2048.pem
server-bridge 192.168.0.50 255.255.255.0 192.168.0.25 192.168.0.30
keepalive 10 120
comp-lzo
max-clients 5
persist-key
persist-tun
status openvpn-status.log
log-append  openvpn.log
verb 4

```

any one knows how i can have a running VPN and have internet access(not via my home gateway but the gateway of the current network) at the same time on the client side.

I think i have to push some routes or change some routes on the client side. I just cant figure out which and how.

---

### Post by SpaceTeddy on 2008-11-26
>      --server-bridge gateway netmask pool-start-IP pool-end-IP

              A helper directive similar to --server which is designed to sim&#8208;
              plify  the  configuration  of  OpenVPN’s server mode in ethernet
              bridging configurations.

              To configure ethernet bridging, you must  first  use  your  OS’s
              bridging  capability to bridge the TAP interface with the ether&#8208;
              net NIC interface.  For example, on Linux this is done with  the
              brctl  tool,  and with Windows XP it is done in the Network Con&#8208;
              nections Panel by selecting the ethernet and  TAP  adapters  and
              right-clicking on "Bridge Connections".

              Next  you you must manually set the IP/netmask on the bridge in&#8208;
              terface.  The gateway and netmask parameters to  --server-bridge
              can  be set to either the IP/netmask of the bridge interface, or
              the IP/netmask of the default gateway/router on the bridged sub&#8208;
              net.

              Finally,  set aside a IP range in the bridged subnet, denoted by
              pool-start-IP and pool-end-IP, for OpenVPN to allocate  to  con&#8208;
              necting clients.

              For  example,  server-bridge  10.8.0.4  255.255.255.0 10.8.0.128
              10.8.0.254 expands as follows:

              mode server
              tls-server

              ifconfig-pool 10.8.0.128 10.8.0.254 255.255.255.0
              push "route-gateway 10.8.0.4"


this is taken directly from the openvpn man page. I have not done this before, but i think your problem is the expansion of the server-bridge directive. As you can read on the bottom, the server-bridge expands to several commands. The last one (push "route-gateway") is what is in your way. In other words, you might need to manually expand the server-bridge in your config and ommit the push gateway. This way, your routing will not be reconfigured and you will still have your old default gatway.
Of course, you might need to push other routes in this case that are being redirected by default with the gateway redirection. 

This is just a guess... i'd have to build myself a testsetup to confirm this...

---

### Post by Lieter on 2008-11-26
nope that isnt it. NM(which i use to connect to the VPN) should keep my default route as default. and only add the route to 192.168.0.0/24 via the tap0 iface. However it totally ***** up my routes. The same problem occurs when I manually launch an openvpn client.

---

### Post by SpaceTeddy on 2008-11-26
mhm... ok. This is gonna be tricky then. Could you maybe supply some more information for me so that i understand the setup better (i don't have the resources at the moment to rebuild it myself, so i will need to get this right in head... somehow).

You've already supplied the routing table before and after the vpn connection... could you also supply the connection log from the client and the server for one dial-up ? Also, i'd like to see the network configuration of the server (ifconfig should suffice) and the servers routing table. Also, for debugging purpose, please use the commandline client only - nm has some pretty strange behaviour with openvpn and needs to be handled carefully once the connection has been established with the commandline (i've had setups where this was not even possible).
so, in short:
 - openvpn logs (client and server)
 - server network configuration
 - server routing information

One more thing - is there a dhcp running on the the subnet with the openvpn server ? This might cause funny behavior as well, since this is embedded and might pull a lease from the dhcp and not from the vpn server!

that's all my ideas for now...

---

