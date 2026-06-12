---
title: "OpenVPN, can connect, can't ping"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by croxis on 2008-06-10
After a good couple hours I finally managed to set up a bridged openvpn server and client on hardy server.  I can connect from inside and outside my network but I can't ping anyone on the network.  From what I have read in various tutorials it seems that it is an issue with firewall or iptables.  As far as I know there is no firewall and webmin says there are no iptables set up. 

Here are the configs

Server:
```
;local 192.168.1.5

daemon
port 1194
proto tcp-server
dev tap0

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/dh1024.pem

server-bridge 192.168.100.1 255.255.255.0 192.168.100.2 192.168.100.100
ifconfig-pool-persist openvpn.dhcp
;ifconfig 192.168.100.1 255.255.255.0


keepalive 10 120
comp-lzo

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log
verb 4
mute 20

;push "route 192.168.100.0 255.255.255.0"
;push "route 192.168.173.0 255.255.255.0"
;push "redirect-gateway def1"

;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
client-to-client
max-clients 10

# plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
# client-cert-not-required
# username-as-common-name

```

Client:
```
##############################################
# Sample client-side OpenVPN 2.0 config file #
# for connecting to multi-client server.     #
#                                            #
# This configuration can be used by multiple #
# clients, however each client should have   #
# its own cert and key files.                #
#                                            #
# On Windows, you might want to rename this  #
# file so it has a .ovpn extension           #
##############################################

# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client

# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
dev tap
;dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
dev-node OpenVPN

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
;proto tcp
;proto udp
proto tcp-client

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote server 1194
;remote my-server-2 1194

# Choose a random host from the remote
# list for load-balancing.  Otherwise
# try hosts in the order specified.
;remote-random

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Downgrade privileges after initialization 

(non-Windows only)
;user nobody
;group nobody

# Try to preserve some state across restarts.
persist-key
persist-tun

# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here.  See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]

# Wireless networks often produce a lot
# of duplicate packets.  Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca ca.crt
cert planata.crt
key planata.key

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
ns-cert-type server

# If a tls-auth key is used on the server
# then every client must also have the key.
;tls-auth ta.key 1

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
;cipher x

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
;mute 20

```

ifconfig
```
br0       Link encap:Ethernet  HWaddr 00:10:dc:6a:df:77
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fe6a:df77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4828350 (4.6 MB)  TX bytes:9575432 (9.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:10:dc:6a:df:77
          inet6 addr: fe80::210:dcff:fe6a:df77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5674762 (5.4 MB)  TX bytes:9669542 (9.2 MB)
          Interrupt:16 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2340151 (2.2 MB)  TX bytes:2340151 (2.2 MB)

tap0      Link encap:Ethernet  HWaddr 00:ff:0d:ae:7e:d2
          inet addr:192.168.100.1  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:dff:feae:7ed2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7298 errors:0 dropped:360 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:71374 (69.7 KB)  TX bytes:1396301 (1.3 MB)


```

Please let me know if more info is needed.  Thank you for any help!

---

### Post by samosamo on 2008-06-10
I don't have time to look into your problem right now, maybe later, but may I suggest having Webmin's OpenVPN module take care of this for you?  I have configured openvpn and ssl keys many times in the past and when I saw how easy it was with webmin I almost cried tears of joy because of how easy it was.

Good luck...

---

### Post by samosamo on 2008-06-10
I took a quick look, don't see anything wrong.  I suggest you look at the client for problems.  I know that Vista has a problem with the tap driver in OpenVPN GUI client.  You need to use the latest beta for it to work.

---

### Post by croxis on 2008-06-10
it isn't a client issue as both windows xp and linux clients can't ping.  As far as I can tell it is a serverside iptables issue, a subject I have never delt with before and I have no idea where to start to even diagnose if that is the problem or not.  Thanks for your help though, and I did get the openvpn webmin module as well for future use.

edit: for my first entry into iptables I typed in the following as su, but no change, i still can't ping server and clients:  

iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT

---

### Post by Sef on 2008-06-10
Moved per OP request.

---

### Post by croxis on 2008-06-21
*polite bump*

Still having the same issue, still would like help figuring out how I am failing :)

---

### Post by croxis on 2008-06-22
I figured out the problem, and for the sake of those who find this thread via search with similar problems I will post my solution.

I am an idiot.

I was under the assumption that the tap/bridged interface would make its own virtual network with its own ip range (so my physical network is 192.168.1.x while the virtual network is 192.168.100.x).  Most of the walkthoughs and tutorials are for the tun (tunnel) which indicate this, so I assumed it wa the case for tap as well.  Nope!  I adjusted my router settings so that the router assigns 10.0.0.2-99 for physical and wireless connections and openvpn assigns 10.0.0.100-200 for virtual connections.  I chose 10.0.0.0 to prevent any conflicts with the popular 192.168 series.  Now it works like a charm!

---

### Post by kacheng on 2008-08-26
croxis,
would you be kind enough to post your final configs?

---

### Post by igpf on 2008-09-13
Hey guys, I'm about to call it on this.  But here's the deal. 
I've installed samba (active as wins) with openvpn.  I was able to connect to the machine from a windows pc and connect no problem.  I was able to push the wins info out and everything.  I can't ping anything.  But i cant connect via remote desktop if i enter the ip address.

when i say ping, i'm refering to ping 'hostname'... the old way.

anyway's i've gone crazy with these forums looking for answers and i get the feeling i'm just missing one little thing... 

the server ip subnet is 192.168.0.0 and the vpn is 172.16.x.x and my home is 192.168.1.x...  

any new ideas, would be greatly appreciated.
thanks...
-ivan

---

### Post by kacheng on 2008-09-14
igpf,

I just solved my similar problems.
Try this instead of the **server** directive:
```
server-bridge 192.168.1.1 255.255.255.0 192.168.1.200 192.168.1.254

```

My dhcp server/gateway (my linksys router in this case) is 192.168.1.1, and it gives out addresses from .100 to .150.  The above directive uses the dhcp server/gateway instead of openvpn to hand out openvpn client addresses in the .200 to .254 range.  I was now able to ping and resolve all clients.
With this directive, using tap interface, I did not have to push any route or gateway or DHCP or WINS information.  i used no push directives whatsoever.

Oh, don't forget to include the client-to-client directive to enable openvpn clients to connect to other computers on the subnet.

```
client-to-client

```

Also, the only firewall configuration I had to do was to open up the openvpn port (in my case UDP 443).

```
iptables -I INPUT -p udp --dport 443 -j ACCEPT

```


Hope that helps.

---

### Post by dujan on 2010-03-10
Hi friends I'm a newbie to linux. I'm trying to setup OpenVpn on Ubuntu being the Server and Windows Server 2003 being the client between to offices but encountered a few problems.
Both location use the 192.168.1.0 subnet 192.168.1.1 being the gateway (modem) on both locations subnet, Lets say everything is the same on both locations subnet. I use ip address for the openvpn thats not in use on either locations subnet. I open up port 1194 on the Sever side Modem/Router in one, Ip tables allows all traffice so its not in use. When i connect the client gets an ip 192.168.1.205. I am not able to ping on either side.  Can someone please assist in setting up Openvpn. I'm a newbie to linux and Openvpn. I'll give my config below

Server Config

mode server
tls-server

local 192.168.1.204 ## ip/hostname of server
port 1194 ## default openvpn port
proto udp



#bridging directive
dev tap0 ## If you need multiple tap devices, add them here
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

persist-key
persist-tun

#certificates and encryption
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0 # This file is secret


cipher BF-CBC        # Blowfish (default)
comp-lzo

#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.204 255.255.255.0 192.168.1.205 192.168.1.211
#push "dhcp-option DNS your.dns.here"
push "dhcp-option DOMAIN your.domain.name.com"
push "route 192.168.1.204 255.255.255.0 192.168.1.1"
max-clients 7 ## set this to the max number of clients that should be connected at a time


#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3


Client config

 ### Client configuration file for OpenVPN\par
\par
# Specify that this is a client\par
client\par
\par
# Bridge device setting\par
dev tap\par
\par
# Host name and port for the server (default port is 1194)\par
# note: replace with the correct values your server set up\par
remote dyndns.org  1194\par
\par
# Client does not need to bind to a specific local port\par
nobind\par
\par
\par
# Keep trying to resolve the host name of OpenVPN server.\par
## The windows GUI seems to dislike the following rule. \par
##You may need to comment it out.\par
resolv-retry infinite\par
\par
# Preserve state across restarts\par
persist-key\par
persist-tun\par
\par
# SSL/TLS parameters - files created previously\par
ca ca.crt\par
cert client.crt\par
key client.key\par
\par
# Since we specified the tls-auth for server, we need it for the client\par
# note: 0 = server, 1 = client\par
tls-auth ta.key 1\par
\par
# Specify same cipher as server\par
cipher BF-CBC\par
\par
# Use compression\par
comp-lzo\par
\par
ip-win32 ipapi\par
\par
# Log verbosity (to help if there are problems)\par
verb 3\par

ifconfig

br0       Link encap:Ethernet  HWaddr 00:11:09:02:5e:f1  
          inet addr:192.168.1.204  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe02:5ef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:753758 (753.7 KB)  TX bytes:112872 (112.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:11:09:02:5e:f1  
          inet6 addr: fe80::211:9ff:fe02:5ef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:853 errors:2 dropped:0 overruns:0 frame:2
          TX packets:761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:772092 (772.0 KB)  TX bytes:106406 (106.4 KB)
          Interrupt:19 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:90:27:fe:18:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42605 (42.6 KB)  TX bytes:42605 (42.6 KB)

tap0      Link encap:Ethernet  HWaddr 1a:86:05:fe:a9:99  
          inet6 addr: fe80::1886:5ff:fefe:a999/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:398 (398.0 B)

---

