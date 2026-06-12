---
title: "OpenVPN, seeing connected clients"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by SBFC on 2007-04-18
Hello all, I have a few questions about OpenVPN.

I have a server set up, with keys for a few of my friends. When connected, we can ping each other successfully using the ips assigned us by OpenVPN. 

However, when attempting to play LAN games over OpenVPN (sole purpose of setting up the server) we are unable to see eachother's games. I'd post information about my setup but I don't know what would be relevant. So anything that would be helpful please let me know and I'd be happy to post it.

Currently we use Hamachi, but would like to move away from it.

---

### Post by joft on 2007-04-18
In your OpenVPN configuration file, do you use "dev tun" or "dev tap"? Most (?) games use UDP broadcast packets to announce game servers. For broadcast to work you need to use "dev tap", which emulates an ethernet device (capable of doing broadcasts). "dev tun" is a pure IP p2p connection (=> no broadcast).

---

### Post by SBFC on 2007-04-18
Thank you very much for the reply. Currently it uses 'dev tun'. 

To set it up using TAP do I need to utilize Ethernet bridging then?

Thanks again. My friends and I were pulling our hair out trying to get this to work.

---

### Post by joft on 2007-04-18
No. You don't need Ethernet Bridging.

Except, if you want to interconnect whole networks with broadcast ability. As long as you just want to interconnect single nodes/computers with OpenVPN you don't need Bridging.

---

### Post by SBFC on 2007-04-18
Alright, thanks to your help we've made some improvements. 

We can now see each other's shares, resolve hostnames...

But game broadcasts still aren't working.

Any other relevant setup info I could provide?

I have it setup as both a tcp and udp server...

---

### Post by joft on 2007-04-21
Hmmm, if you can see shares, broadcast works, because the so called "browsing" is done via broadcast. I assume you mean Samba shares or shares of a real M$ Windows machines and you **don't have** a WINS server, right?

You need one server, only. I'd recommend using UDP, especially for games.

Do you use a firewall? Or some/one of your peers? You could use wireshark/ethereal to determine, if there is broadcast traffic - perhaps a problem with the specific game not recognizing data packets.

---

### Post by spacedoggy on 2008-04-07
I'm having similar problems setting up games on openVPN

specifically we have set up a default multi client PKI setup using tun devices

the game were trying to get working is starcraft which uses UDP broadcasts on a Local network to locate games.

I'm going to try to change to tap adaptors later today and see if that works.

I read somewhere that bridging was necessary for this to work, but it seems very difficult to set up, is it?

I don't understand why bridging would be necessary with openVPN while Hamanchi works out of the box with this game and many others? it's a classic example of free (as in speech) software being rock hard to configure compared to it's evil oppressing counterpart.

---

### Post by spacedoggy on 2008-04-20
ok, sorry for the delay in my promised response, my hard drive went bye last week and I just got all my stuff back up. 

ok, changed tun to tap devices, no bridging was necessary and udp broadcasting in starcraft worked for me and 4 clients, there was a little lag, but I'd say that was due to limited bandwidth and a wifi connection on the server. it'll be fine on a proper server with a stable connection I'd say.

thanks for your help on this joft

---

### Post by inportb on 2008-05-21
I've run into a similar problem. I have the tap device set up, without bridging; the reason is that I do not want to merge two networks, but set up a virtual LAN of sorts. I can ping across the VPN, but not broadcast. Running tcpdump on the server (10.10.0.1 on VPN) while pinging from a client (10.10.0.2 on VPN), I find that the server does receive the request, but does not respond and does not forward them to the other clients:

> client$ ping 10.10.0.1
PING 10.10.0.1 (10.10.0.1) 56(84) bytes of data.
64 bytes from 10.10.0.1: icmp_seq=1 ttl=64 time=14.0 ms
64 bytes from 10.10.0.1: icmp_seq=2 ttl=64 time=12.6 ms
64 bytes from 10.10.0.1: icmp_seq=3 ttl=64 time=34.8 ms
64 bytes from 10.10.0.1: icmp_seq=4 ttl=64 time=20.1 ms
--- 10.10.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 12.362/13.601/14.560/0.841 ms

server$ sudo tcpdump -i tap0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on tap0, link-type EN10MB (Ethernet), capture size 96 bytes
00:55:53.393081 IP 10.10.0.2 > 10.10.0.1: ICMP echo request, id 6686, seq 1, length 64
00:55:53.396288 IP 10.10.0.1 > 10.10.0.2: ICMP echo reply, id 6686, seq 1, length 64
00:55:54.393010 IP 10.10.0.2 > 10.10.0.1: ICMP echo request, id 6686, seq 2, length 64
00:55:54.393075 IP 10.10.0.1 > 10.10.0.2: ICMP echo reply, id 6686, seq 2, length 64
00:55:55.392798 IP 10.10.0.2 > 10.10.0.1: ICMP echo request, id 6686, seq 3, length 64
00:55:55.392861 IP 10.10.0.1 > 10.10.0.2: ICMP echo reply, id 6686, seq 3, length 64
00:55:56.392848 IP 10.10.0.2 > 10.10.0.1: ICMP echo request, id 6686, seq 4, length 64
00:55:56.392915 IP 10.10.0.1 > 10.10.0.2: ICMP echo reply, id 6686, seq 4, length 64

> client$ ping -b 10.10.0.0
WARNING: pinging broadcast address
PING 10.10.0.0 (10.10.0.0) 56(84) bytes of data.
--- 10.10.0.0 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3010ms

server$ sudo tcpdump -i tap0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on tap0, link-type EN10MB (Ethernet), capture size 96 bytes
00:56:58.793938 IP 10.10.0.2 > 10.10.0.0: ICMP echo request, id 13854, seq 1, length 64
00:56:59.804022 IP 10.10.0.2 > 10.10.0.0: ICMP echo request, id 13854, seq 2, length 64
00:57:00.801878 IP 10.10.0.2 > 10.10.0.0: ICMP echo request, id 13854, seq 3, length 64
00:57:01.804087 IP 10.10.0.2 > 10.10.0.0: ICMP echo request, id 13854, seq 4, length 64

Any ideas? And would anyone who has gotten this working please post his/her server and client config files?

---

### Post by SBFC on 2008-05-21
With the below config file my friends and I were able to view shares and play lan games...

```

###########################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
# configurations (See the Examples page         #
# on the web site for more info).               #
#                                               #
# This config should work on Windows            #
# or Linux/BSD systems.  Remember on            #
# Windows to quote pathnames and use            #
# double backslashes, e.g.:                     #
# "C:\\Program Files\\OpenVPN\\config\\foo.key" #
#                                               #
# Comments are preceded with '#' or ';'         #
#################################################

management localhost 7505

# Which local IP address should OpenVPN
# listen on? (optional)
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
;proto tcp
proto udp

# "dev tun" will create a routed IP tunnel,
# "dev tap" will create an ethernet tunnel.
# Use "dev tap0" if you are ethernet bridging
# and have precreated a tap0 virtual interface
# and bridged it with your ethernet interface.
# If you want to control access policies
# over the VPN, you must create firewall
# rules for the the TUN/TAP interface.
# On non-Windows systems, you can give
# an explicit unit number, such as tun0.
# On Windows, use "dev-node" for this.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
dev tap0
;dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel if you
# have more than one.  On XP SP2 or higher,
# you may need to selectively disable the
# Windows firewall for the TAP adapter.
# Non-Windows systems usually don't need this.
;dev-node MyTap

# SSL/TLS root certificate (ca), certificate
# (cert), and private key (key).  Each client
# and the server must have their own cert and
# key file.  The server and all clients will
# use the same ca file.
#
# See the "easy-rsa" directory for a series
# of scripts for generating RSA certificates
# and private keys.  Remember to use
# a unique Common Name for the server
# and each of the client certificates.
#
# Any X509 key management system can be used.
# OpenVPN can also use a PKCS #12 formatted key file
# (see "pkcs12" directive in man page).
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/macabre.crt
key /etc/openvpn/easy-rsa/keys/macabre.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh /etc/openvpn/easy-rsa/keys/dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

# Maintain a record of client <-> virtual IP address
# associations in this file.  If OpenVPN goes down or
# is restarted, reconnecting clients can be assigned
# the same virtual IP address from the pool that was
# previously assigned.
ifconfig-pool-persist ipp.txt

# Configure server mode for ethernet bridging.
# You must first use your OS's bridging capability
# to bridge the TAP interface with the ethernet
# NIC interface.  Then you must manually set the
# IP/netmask on the bridge interface, here we
# assume 10.8.0.4/255.255.255.0.  Finally we
# must set aside an IP range in this subnet
# (start=10.8.0.50 end=10.8.0.100) to allocate
# to connecting clients.  Leave this line commented
# out unless you are ethernet bridging.
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
;server-bridge 192.168.1.175 255.255.255.0 192.168.1.200 192.168.1.250
;server-bridge 10.8.0.1 255.255.255.0 10.8.0.200 10.8.0.250

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"

# To assign specific IP addresses to specific
# clients or if a connecting client has a private
# subnet behind it that should also have VPN access,
# use the subdirectory "ccd" for client-specific
# configuration files (see man page for more info).

# EXAMPLE: Suppose the client
# having the certificate common name "Thelonious"
# also has a small subnet behind his connecting
# machine, such as 192.168.40.128/255.255.255.248.
# First, uncomment out these lines:
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
# Then create a file ccd/Thelonious with this line:
#   iroute 192.168.40.128 255.255.255.248
# This will allow Thelonious' private subnet to
# access the VPN.  This example will only work
# if you are routing, not bridging, i.e. you are
# using "dev tun" and "server" directives.

# EXAMPLE: Suppose you want to give
# Thelonious a fixed VPN IP address of 10.9.0.1.
# First uncomment out these lines:
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
# Then add this line to ccd/Thelonious:
#   ifconfig-push 10.9.0.1 10.9.0.2

# Suppose that you want to enable different
# firewall access policies for different groups
# of clients.  There are two methods:
# (1) Run multiple OpenVPN daemons, one for each
#     group, and firewall the TUN/TAP interface
#     for each group/daemon appropriately.
# (2) (Advanced) Create a script to dynamically
#     modify the firewall in response to access
#     from different clients.  See man
#     page for more info on learn-address script.
;learn-address ./script

# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
push "dhcp-option DNS 10.8.0.1"
push "dhcp-option WINS 10.8.0.1"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
client-to-client

# Uncomment this directive if multiple clients
# might connect with the same certificate/key
# files or common names.  This is recommended
# only for testing purposes.  For production use,
# each client should have its own certificate/key
# pair.
#
# IF YOU HAVE NOT GENERATED INDIVIDUAL
# CERTIFICATE/KEY PAIRS FOR EACH CLIENT,
# EACH HAVING ITS OWN UNIQUE "COMMON NAME",
# UNCOMMENT THIS LINE OUT.
;duplicate-cn

# The keepalive directive causes ping-like
# messages to be sent back and forth over
# the link so that each side knows when
# the other side has gone down.
# Ping every 10 seconds, assume that remote
# peer is down if no ping received during
# a 120 second time period.
keepalive 10 120

# For extra security beyond that provided
# by SSL/TLS, create an "HMAC firewall"
# to help block DoS attacks and UDP port flooding.
#
# Generate with:
#   openvpn --genkey --secret ta.key
#
# The server and each client must have
# a copy of this key.
# The second parameter should be '0'
# on the server and '1' on the clients.
;tls-auth ta.key 0 # This file is secret

# Select a cryptographic cipher.
# This config item must be copied to
# the client config file as well.
;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

# Enable compression on the VPN link.
# If you enable it here, you must also
# enable it in the client config file.
comp-lzo

# The maximum number of concurrently connected
# clients we want to allow.
;max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
;user nobody
;group nobody

# The persist options will try to avoid
# accessing certain resources on restart
# that may no longer be accessible because
# of the privilege downgrade.
persist-key
persist-tun

# Output a short status file showing
# current connections, truncated
# and rewritten every minute.
status openvpn-status.log

# By default, log messages will go to the syslog (or
# on Windows, if running as a service, they will go to
# the "\Program Files\OpenVPN\log" directory).
# Use log or log-append to override this default.
# "log" will truncate the log file on OpenVPN startup,
# while "log-append" will append to it.  Use one
# or the other (but not both).
;log         openvpn.log
log-append  openvpn.log

# Set the appropriate level of log
# file verbosity.
#
# 0 is silent, except for fatal errors
# 4 is reasonable for general usage
# 5 and 6 can help to debug connection problems
# 9 is extremely verbose
verb 3

# Silence repeating messages.  At most 20
# sequential messages of the same message
# category will be output to the log.
;mute 20


```

---

### Post by inportb on 2008-05-22
Thanks man, I shall try this out now.
Thanks also to spacedoggy for sending me some config files.

### EDIT ###

I see that I had a working setup all along, and that my problem was completely unrelated:

I have a VPN on 10.10.0.0 255.255.255.0, where the server/gateway is at 10.10.0.1. I was pinging the "broadcast" addresses 10.10.0.0 and 10.10.0.255 hoping that all clients would receive the ICMP packets and respond. As it turns out, the server picked up all these packets (and everything else destined for 10.10.0.*, as expected), but was not forwarding the 0/255 packets to any of the other clients; it was responding only to packets destined for 10.10.0.1.

I'll do some additional research on how to get the server to forward packets received on these special addresses, or at least respond to them.

---

