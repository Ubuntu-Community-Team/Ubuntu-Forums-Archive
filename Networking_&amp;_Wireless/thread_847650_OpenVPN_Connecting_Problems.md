---
title: "OpenVPN Connecting Problems"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by tjwallace on 2008-07-02
I can't connect to my DD-WRT openvpn server through either the command line or NetworkManager.

With the command line is just stops after *Initialization Sequence Completed*.  I can use *sudo ifconfig -a* to see the tap0 device created, and then call *sudo dhclient tap0* to get an ip address from the VPN router but I think the routes screw up as I cannot browse the internet after that.  I can however ping my local router.
The command line output is:
```

jeff@tjwallace:~$ sudo openvpn --config config.ovpn
[sudo] password for jeff: 
Wed Jul  2 15:08:02 2008 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Enter Private Key Password:
Wed Jul  2 15:08:05 2008 WARNING: file 'client1.key' is group or others accessible
Wed Jul  2 15:08:05 2008 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Wed Jul  2 15:08:05 2008 LZO compression initialized
Wed Jul  2 15:08:05 2008 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Jul  2 15:08:05 2008 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Wed Jul  2 15:08:05 2008 Local Options hash (VER=V4): 'd79ca330'
Wed Jul  2 15:08:05 2008 Expected Remote Options hash (VER=V4): 'f7df56b8'
Wed Jul  2 15:08:05 2008 Socket Buffers: R=[110592->131072] S=[110592->131072]
Wed Jul  2 15:08:05 2008 UDPv4 link local: [undef]
Wed Jul  2 15:08:05 2008 UDPv4 link remote: *.*.*.*:1194
Wed Jul  2 15:08:05 2008 TLS: Initial packet from *.*.*.*:1194, sid=3ff9b8b9 32a2bf62
Wed Jul  2 15:08:06 2008 VERIFY OK: depth=1, /C=*/ST=*/L=*/O=*/CN=*/emailAddress=*
Wed Jul  2 15:08:06 2008 VERIFY OK: nsCertType=SERVER
Wed Jul  2 15:08:06 2008 VERIFY OK: depth=0, /C=*/ST=*/O=*/CN=server/emailAddress=*
Wed Jul  2 15:08:07 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Jul  2 15:08:07 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Jul  2 15:08:07 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Jul  2 15:08:07 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Jul  2 15:08:07 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Jul  2 15:08:07 2008 [server] Peer Connection Initiated with *.*.*.*:1194
Wed Jul  2 15:08:09 2008 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Wed Jul  2 15:08:09 2008 PUSH: Received control message: 'PUSH_REPLY,ping 15,ping-restart 60'
Wed Jul  2 15:08:09 2008 OPTIONS IMPORT: timers and/or timeouts modified
Wed Jul  2 15:08:09 2008 TUN/TAP device tap0 opened
Wed Jul  2 15:08:09 2008 TUN/TAP TX queue length set to 100
Wed Jul  2 15:08:24 2008 Initialization Sequence Completed

```

If I use the network manager I get the following error message:
> 
Could not start the VPN connection * because the VPN server did not return an adequate network configuration.

The VPN login failed because the VPN program received an invalid configuration from the VPN server


This is from syslog:
```

Jul  2 15:11:58 tjwallace NetworkManager: <info>  Will activate VPN connection '*', service 'org.freedesktop.NetworkManager.openvpn', user_name 'jeff', vpn_data 'connection-type / x509 / dev / tap / remote / * / port / 1194 / proto / udp / servercert-insecure / yes / ca / */ca.crt / cert / */client1.crt / key / */client1.key / comp-lzo / yes / shared-key /  / local-ip /  / remote-ip /  / username / ', route '192.168.2.0/24'. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 1 of 4 (Connection Prepare) scheduled... 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.openvpn (PID 10002) 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 1 of 4 (Connection Prepare) complete. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 1 -> 6. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 3 of 4 (Connect) scheduled... 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 3 of 4 (Connect) sending connect request. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 6 -> 3. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 3 of 4 (Connect) reply received. 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jul  2 15:11:58 tjwallace NetworkManager: <info>  VPN Activation (*) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jul  2 15:11:58 tjwallace nm-openvpn[10005]: OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Jul  2 15:11:58 tjwallace nm-openvpn[10005]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Jul  2 15:11:59 tjwallace nm-openvpn[10005]: WARNING: file '*/client1.key' is group or others accessible
Jul  2 15:11:59 tjwallace nm-openvpn[10005]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Jul  2 15:11:59 tjwallace nm-openvpn[10005]: LZO compression initialized
Jul  2 15:11:59 tjwallace nm-openvpn[10005]: UDPv4 link local: [undef]
Jul  2 15:11:59 tjwallace nm-openvpn[10005]: UDPv4 link remote: *.*.*.*:1194
Jul  2 15:12:00 tjwallace nm-openvpn[10005]: [server] Peer Connection Initiated with *.*.*.*:1194
Jul  2 15:12:01 tjwallace nm-openvpn[10005]: TUN/TAP device tap1 opened
Jul  2 15:12:01 tjwallace nm-openvpn[10005]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tap1 1500 1574   init
Jul  2 15:12:01 tjwallace nm-openvpn-service-openvpn-helper: <WARNING>^I main (): nm-openvpn-service-openvpn-helper didn't receive an Internal IP4 Address from openvpn. 
Jul  2 15:12:01 tjwallace NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.openvpn', signal 'IPConfigBad', with message 'The VPN login failed because the VPN program received an invalid configuration from the VPN server.'. 
Jul  2 15:12:01 tjwallace nm-openvpn[10005]: script failed: shell command exited with error status: 1
Jul  2 15:12:01 tjwallace NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 3 -> 5. 
Jul  2 15:12:01 tjwallace nm-openvpn[10005]: Exiting
Jul  2 15:12:01 tjwallace NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 5 -> 6. 
Jul  2 15:12:01 tjwallace NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.openvpn): could not stop connection '*' because service was 6. 

```

Server Config:
```

# Tunnel options
mode server       # Set OpenVPN major mode
proto udp         # Setup the protocol (server)
port 1194         # TCP/UDP port number
dev tap0          # TUN/TAP virtual network device
keepalive 15 60   # Simplify the expression of --ping 
daemon            # Become a daemon after all initialization
verb 3            # Set output verbosity to n 
comp-lzo          # Use fast LZO compression 

# OpenVPN server mode options
client-to-client  # tells OpenVPN to internally route 
duplicate-cn      # Allow multiple clients with the same common 

# TLS Mode Options
tls-server        # Enable TLS and assume server role during TLS 
ca ca.crt         # Certificate authority (CA) file
dh dh1024.pem     # File containing Diffie Hellman parameters 
cert server.crt   # Local peer's signed certificate
key server.key    # Local peer's private key 
status openvpn-status.log

```

Client Config:
```

client
dev tap
proto udp
remote *.*.*.* 1194
resolv-retry infinite
nobind
float
persist-key
persist-tun
ca ca.crt
cert client1.crt
key client1.key
ns-cert-type server
comp-lzo
verb 3
pull
ping 10
ping-restart 60
route-delay 15

```

I can use the OpenVPN GUI on a windows virtual machine and connect fine.

Do I have to enable some sort of DHCP push on the server config file?

---

### Post by tjwallace on 2008-07-03
bump

---

### Post by tjwallace on 2008-07-04
another bump...

---

### Post by SpaceTeddy on 2008-07-04
mhm - interesting. What is your aim to do with the vpn ?

If i read your configuration correctly, then you are using a layer 2 vpn which is, on the serverside, not bridged or embedded into a real network. This means you will (most likely) need an external dhcp server running there. As i said, the vpn is layer to enabled (or so i see it) so what really happens is you plug a "cable" from the client to the server directly (this is the vpn connection). But as neither the client nor the server have any configuration for the network they just leave the devices unconfigured. 

Now, network manage will, if it does not receive an ip-configuration, abort the connection as it thinks the connections to be useless. If this is a bug or a feature i don't know, but then there are a few things that i don't really like about network manager. 

So - there are two ways to fix this. 

1.) If you don't need layer 2, but only IP based protocols and no broadcasts (i.e. no games over the vpn) then i would suggest you modify your config to switch from tap to tun device. That one automatically configured the end points with the build-in dhcp server from openvpn. It's a lot less hassle and it saves bandwidth.

2.) if you do need broadcasting, then you will need to configure the serverside tap device properly by either embedding it into the servers real network or making the server a router which separates the vpn from the real network. So, this boils down to

2a.) Bridges VPN. 
Create a bridge holding the real network (eth0) and the server device (tap0) to embed the client into the real network. 

2b.) Routed VPN
modify your openvpn configuration to have a proper IP address, install the dhcp-server and tell it to listen on the tap0 device. Also, If you want to access the internet over this connection, then you will need to enable ip_forwarding, set a couple of routes (on the machine it self as well as your default gateway) and allow pakets to pass through the vpn-server.

i hope i did not confuse you too much :)

If any questions remain - please don't hesitate to ask
PS: if you don't need broacast support i would really suggest you use the tun device...

---

### Post by tjwallace on 2008-07-04
I believe I am already running a bridged/tap setup that puts vpn clients in the real network.  Here is the full script that is run by the DD-WRT router:
```

cd /tmp
openvpn --mktun --dev tap0
brctl addif br0 tap0
ifconfig tap0 0.0.0.0 promisc up

echo "
# Tunnel options
mode server       # Set OpenVPN major mode
proto udp         # Setup the protocol (server)
port 1194         # TCP/UDP port number
dev tap0          # TUN/TAP virtual network device
keepalive 15 60   # Simplify the expression of --ping 
daemon            # Become a daemon after all initialization
verb 3            # Set output verbosity to n 
comp-lzo          # Use fast LZO compression 

# OpenVPN server mode options
client-to-client  # tells OpenVPN to internally route 
duplicate-cn      # Allow multiple clients with the same common 

# TLS Mode Options
tls-server        # Enable TLS and assume server role during TLS 
ca ca.crt         # Certificate authority (CA) file
dh dh1024.pem     # File containing Diffie Hellman parameters 
cert server.crt   # Local peer's signed certificate
key server.key    # Local peer's private key 
status openvpn-status.log
" > openvpn.conf

echo "
-----BEGIN CERTIFICATE-----
*
-----END CERTIFICATE-----
" > ca.crt
echo "
-----BEGIN RSA PRIVATE KEY-----
*
-----END RSA PRIVATE KEY-----
" > server.key
chmod 600 server.key
echo "
-----BEGIN CERTIFICATE-----
*
-----END CERTIFICATE-----
" > server.crt
echo "
-----BEGIN DH PARAMETERS-----
*
-----END DH PARAMETERS-----
" > dh1024.pem

sleep 5
ln -s /usr/sbin/openvpn /tmp/myvpn
/tmp/myvpn --config openvpn.conf

```

As I said before, if I use a Windows box to connect to the VPN, it will pull a DHCP address no problem (the same address range the the router would give to local clients).

---

### Post by SpaceTeddy on 2008-07-04
mhm - very interesting. And sorry for misunderstanding you. I tend to explain to much and exepect to little from people. Must be the teacher in me :)

Anyways, your setup looks rather good like this - and you say that a windows machine (i guess you're using openvpn-gui ?) will putt an ip-address with a problem ? Then, i am out of ideas, really.
I have never setup a VPN like that before and therefore have no experience with it. I have only used tun devices so far - or configured static bridges between routers to span networks over the internet. 
Just one question tho - do you also add the physical device to your bridge ? as i can see, you only add tap0 - you'll need the physical device in it as well. But i guess you did that and just did not post it :)

I'll sleep and think over it, and if i have a reevation i will share it. Otherwise, i am pretty stumped here too (without a test setup). Maybe i'll build myself one on the weekend (if i find the time).

sorry again for the wrong answer...

---

### Post by tjwallace on 2008-07-04
yes on windows I use openvpn-gui.  I can actually get an IP from the router if I do a *sudo dhclient tap0*, but then all the routes go wild and nothing works.  My local network is 192.168.1.x and my remote network is 192.168.2.x.  Here is my route tables from before and after:

Before:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

After (command line openvpn connection):
```

jeff@tjwallace:~$ sudo dhclient tap0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/tap0/00:ff:39:7c:18:d2
Sending on   LPF/tap0/00:ff:39:7c:18:d2
Sending on   Socket/fallback
DHCPDISCOVER on tap0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.2.123 from 192.168.2.1
DHCPREQUEST of 192.168.2.123 on tap0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.123 from 192.168.2.1
bound to 192.168.2.123 -- renewal in 35136 seconds.
jeff@tjwallace:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 tap0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 tap0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Thanks for your help.

---

### Post by SpaceTeddy on 2008-07-04
now that is a good hint. As far as i can see, you are creating a routing loop here. look at the gateway (actually, there should only be ONE default gateway... really).
So, here is what i think happens. 
When you connect to the vpn, the dhcp server from the attached lan issues a normal dhcp lease. As this lease also contains a default gateway you get the second one added. Why this one is first in your routing table i don't really know... but there are two things wrong. 

1.) you should ALWAYS, ALWAYS have a route to the vpn server. This means, there should always be an entry in your routing table so that the acctually connection to the vpn server can exist. In your routing table, there is no such route. 

2.) Your default gateway should be overwritten - not added ! on any machine there should only be one default gateway active. 

So, what happens ?
Your client initiates the connection to the vpn server
The new default gateway get added routing all traffic over the vpn. Since this really is ALL traffic, the vpn-client on your machine now tries to utilize the vpn connection to contact the vpn-server. And this is were the routing loop exists. There is one exception to routing all traffic over the vpn - you must NEVER EVER route the vpn-server itself over the vpn. 

This said, i will assume in the following example that your vpn-server has the ip 1.2.3.4. Try the following as a test run to see if i am somewhere near the solution of the problem.

first, connect the vpn. Please note that you only have 60 seconds until the connection times out. So you must issue the following commands within those 60 seconds. Also, remember that 1.2.3.4 is an example IP and needs to be replaced by the real ip of your vpn-server.

```
sudo route add -net 1.2.3.4 netmask 255.255.255.255 gw 192.168.1.1
sudo route del -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.1.1
```

I hope that in my degraded state of mind i am still able to think this through properly. The first line should add the route to your vpn server and make sure the routing loop does not occur, the second should delete the now obsolete default gateway leaving you only with the vpn.

Good thinking posting this output :)

---

### Post by tjwallace on 2008-07-05
Thanks for the continued help SpaceTeddy, I think we are getting on the right track.  However I don't want all trafic routed over the VPN link, just traffic to 192.168.2.x.

I'll try to give you a layout of the network...
Local:
Range: 192.168.1.x
Router: 192.168.1.1

Remote:
Range: 192.168.2.x
Router: 192.168.2.1

So I think what I need to do is set a static 192.168.2.x address to the tap device and then setup a route so that all 192.168.2.x traffic will get routed through the tap.  Or maybe there is a way to get DHCP on the tap device without messing around with the route table?  Or maybe I can create a bridge to bridge eth0 and tap0 together?

---

### Post by SpaceTeddy on 2008-07-05
So, if i understand that right - you only want connection from the vpn to the normal network. Also, the "normal" network is NOT in the same range as the vpn is ? 

I have an idea how to accomplish this, but don't have the time to write it down now. Gimme a day and i'll (most likely) be able to write down some steps for you to do. Meanwhile, try this route command and see if that has the desired effect:

```
sudo route del -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.2.1
```

that should remove the redirection over the vpn and only route the 192.168.2.0/x over it. Everything else should work normally afterwards. If that fixes the problem, then i have two solutions for the problem :)

Also, you should think about using the "server-bridge" command in the server config of the openvpn. That should allow you to assign the ip's properly without having to have an external dhcp.
Also, i still think that you should be using the tun device and only have layer 3 routing. But that is my opinion...

---

### Post by tjwallace on 2008-07-05
Yes I only use the VPN to talk to computers on the remote network, not to route all my traffic.  However on another note I GOT IT WORKING!

Just before you posted I used the following commands and was able fully connect to the VPN!
```

$ sudo openvpn --config config.ovpn
$ sudo ifconfig tap0 192.168.2.10 netmask 255.255.255.0 up
$ sudo route add -net 192.168.2.0 netmask 255.255.255.0 tap0

```

I then found out you can use the line *up ./up.sh* in the client config file to make openvpn run the script once the connection is made.

Still not the best solution, and I think I will have to do something with the server-bridge command like you suggested.

This page ([http://openvpn.net/index.php/documentation/faq.html#bridge-addressing](http://openvpn.net/index.php/documentation/faq.html#bridge-addressing)) says: > The one complexity about this configuration is that you need to modify your DHCP server configuration to differentiate between local clients and VPN clients. The reason for this is that you must not pass out a default gateway to VPN clients.
This is what is happening now when I run *dhclient tap0*.  I will have to lookup how to use "server-bridge" like you suggested and begin testing.

---

