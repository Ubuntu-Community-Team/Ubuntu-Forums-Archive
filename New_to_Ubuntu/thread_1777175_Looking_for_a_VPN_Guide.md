---
title: "Looking for a VPN Guide"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Chrissd on 2011-06-07
Hi,

Can anyone recommend me a VPN guide please? I don't understand the concept very well, other than securely pretending line you're on a local network. All the guides I've seen involve Windows or older versions of Ubuntu. I'm running Natty, which apparently has preinstalled VPN support. I found this guide [here](https://help.ubuntu.com/community/SSH_VPN), but it talks about bridging a connection? Unfortunately, I only have one network card, not two, so I've nothing to bridge?

I basically want to be able to connect securely to my home network from the outside world, this way I can print and access other machines easily. I use SSH at the moment, if that's any use.

Do I understand it right I need to configure my main computer at home to act as the VPN server, which my netbook will then connect to? There's no DHCP on my home network, will that cause an issue?

Thanks for any advice!

---

### Post by ubudog on 2011-06-08
I used the official guide (I believe it's the official guide), and as a total OpenVPN noob, I got my server set up and running with clients in 2 days.

[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

It may seem a bit hard at first, but keep reading on.  Let me know if you have any questions about it, as I have already gone through it.  :)

---

### Post by Chrissd on 2011-06-09
Below is what happens, I'm not sure what's actually going on as to what to check.

```
Thu Jun  9 12:09:01 2011 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jun  9 12:09:01 2011 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Jun  9 12:09:01 2011 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jun  9 12:09:01 2011 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Thu Jun  9 12:09:01 2011 [server] Peer Connection Initiated with [AF_INET]SERVER:PORT
Thu Jun  9 12:09:04 2011 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Thu Jun  9 12:09:04 2011 PUSH: Received control message: 'PUSH_REPLY,route-gateway 10.8.0.1,ping 10,ping-restart 120,ifconfig 10.8.0.2 255.255.255.0'
Thu Jun  9 12:09:04 2011 OPTIONS IMPORT: timers and/or timeouts modified
Thu Jun  9 12:09:04 2011 OPTIONS IMPORT: --ifconfig/up options modified
Thu Jun  9 12:09:04 2011 OPTIONS IMPORT: route-related options modified
Thu Jun  9 12:09:04 2011 Note: Cannot ioctl TUNSETIFF tap: Operation not permitted (errno=1)
Thu Jun  9 12:09:04 2011 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Thu Jun  9 12:09:04 2011 Cannot allocate TUN/TAP dev dynamically
Thu Jun  9 12:09:04 2011 Exiting

```

ifconfig then shows
```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Chrissd on 2011-06-09
Ok, just realised I can ping the other VPN IP address. Does that mean it's working?

I was hoping to use the VPN to be able to print documents from different networks. How could I do this?

---

### Post by ubudog on 2011-06-09
> **Chrissd said:**
> Below is what happens, I'm not sure what's actually going on as to what to check.

```
Thu Jun  9 12:09:01 2011 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jun  9 12:09:01 2011 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Jun  9 12:09:01 2011 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jun  9 12:09:01 2011 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Thu Jun  9 12:09:01 2011 [server] Peer Connection Initiated with [AF_INET]SERVER:PORT
Thu Jun  9 12:09:04 2011 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Thu Jun  9 12:09:04 2011 PUSH: Received control message: 'PUSH_REPLY,route-gateway 10.8.0.1,ping 10,ping-restart 120,ifconfig 10.8.0.2 255.255.255.0'
Thu Jun  9 12:09:04 2011 OPTIONS IMPORT: timers and/or timeouts modified
Thu Jun  9 12:09:04 2011 OPTIONS IMPORT: --ifconfig/up options modified
Thu Jun  9 12:09:04 2011 OPTIONS IMPORT: route-related options modified
Thu Jun  9 12:09:04 2011 Note: Cannot ioctl TUNSETIFF tap: Operation not permitted (errno=1)
Thu Jun  9 12:09:04 2011 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Thu Jun  9 12:09:04 2011 Cannot allocate TUN/TAP dev dynamically
Thu Jun  9 12:09:04 2011 Exiting

```

Is that what you see on your server or client?

---

### Post by ubudog on 2011-06-09
Hi there.  Try from scratch, using the guide here by SpaceTeddy:
[http://ubuntuforums.org/showthread.php?t=812065&highlight=openvpn+printing](http://ubuntuforums.org/showthread.php?t=812065&highlight=openvpn+printing)

When you're setting up OpenVPN, you may have to start from scratch a bunch.  It's very complicated.  :-)

---

### Post by Chrissd on 2011-06-10
Thanks! Very good guide. You're right about this being complex. All this because my university charge 5p for a sheet of paper.

I boot up my netbook and tun0-00 is there. Should I have to use "openvpn /etc/openvpn/client.conf" at all?

Netstat shows:
```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
 
Everything works fine apart from now trying to contact the network. Even pings fail apart from to the internet and the VPN server (10.8.0.1)

I've now got no idea what could be wrong. I've put the ```
push "route 192.168.0.0 255.255.255.0"
```

iptables was mentioned, but that only mentions fail2ban, everything else is allowed, so that can't be the issue?

Perhaps I should switch degrees courses to something involving computers.

---

### Post by Chrissd on 2011-06-10
I found a guide talking about the command route -n, but nothing about fixing it. Not even sure what it's really saying.
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
192.168.0.0     10.8.0.5        255.255.255.0   UG    0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```
I'm fairly certain that 10.8.0.5 doesn't exist? Is that the problem?

---

### Post by ubudog on 2011-06-10
Wow, this is complicated.  Once you have OpenVPN correctly configured on the netbook, you can just run:
```
sudo service openvpn start
```

Now, first things first.  Make sure your server is up and running.  Start OpenVPN on the netbook.  You have the certs and everything set up, right?

Assuming your server is 10.8.0.1, run this on your netbook: (after starting OpenVPN)

```
ping 10.8.0.1
``` 

If nothing comes back, the vpn is not up... let me know how it goes.

---

### Post by Chrissd on 2011-06-10
Yep, from the NetBook (10.8.0.6) I can ping the server at 10.8.0.1! [img]http://www.blue-room.org.uk/public/style_emoticons/default/thumbup.gif[/img]

---

### Post by ubudog on 2011-06-10
> **Chrissd said:**
> Yep, from the NetBook (10.8.0.6) I can ping the server at 10.8.0.1! [img]http://www.blue-room.org.uk/public/style_emoticons/default/thumbup.gif[/img]

GREAT!  I'm surprised at how fast you got that working!  Seems like it's up.

Now, for the printing.  Assuming the server is at your home, and you don't move it around...

Plug the printer you want to use into a machine on your home network.  Be sure to add that machine to your OpenVPN network too.  (create certs for it, etc.)  Once the machine with the printer is on the vpn, you can ssh into it and start openoffice to access the documents on it and print them.

```
ssh -X user@ipaddress
```
(note the -X for running openoffice and other GUI apps)

I hope that helps you, if you have any questions please feel free to post.

PS: For ssh security, I recommend turning off password authorization on all the machines you connect to, and use keys.  Here is a guide for that:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

PSS: If someone else here has a better explanation of what to do, please post!  I'm not always correct.  :p

---

### Post by Chrissd on 2011-06-10
Well, that's one way of doing it! Certainly works. Just need to work out what all the command lines for the programs I use are! Interested to hear if there's another way of doing it!

My printer has it's own IP on the router.

---

### Post by ubudog on 2011-06-10
I will try to do some searching and see if I can find a better way.

So your VPN is up and working?

---

### Post by Chrissd on 2011-06-11
> **ubudog said:**
> I will try to do some searching and see if I can find a better way.

So your VPN is up and working?

Yeah, I can SSH into my server through the VPN. I just can't contact my 192.168.0.0 network through it.

---

### Post by Chrissd on 2011-06-14
I'm going to start a new thread asking the specific question just to get this last step sorted.

Thanks for your help in getting it started! :)

---

### Post by ubudog on 2011-06-14
No problem, glad to help.  If you want, link the new thread here, I may be able to help there too.  :-)

---

### Post by SeijiSensei on 2011-06-14
> **Chrissd said:**
> Yeah, I can SSH into my server through the VPN. I just can't contact my 192.168.0.0 network through it.

First, the routing table you reported above has two routes to 192.168.0.0/24, one directly via the wifi card and the other via the VPN.  I suggest removing the route via the VPN; it's probably created via a script that's run from the "up" directive in the openvpn.conf file.

Once that's done, you'll probably also need to enable IP forwarding on the server.  First run "cat /proc/sys/net/ipv4/ip_forward"; if it returns zero, forwarding between interfaces is disabled.  You can turn it on for the current session by running "echo '1' > /proc/sys/net/ipv4/ip_forward", but to make the change permanent you need to edit /etc/sysctl.conf and enable the "net.ipv4.ip_forward=1" directive.

---

### Post by Chrissd on 2011-06-14
> **SeijiSensei said:**
> you'll probably also need to enable IP forwarding on the server.  First run "cat /proc/sys/net/ipv4/ip_forward"; if it returns zero, forwarding between interfaces is disabled.It does! Sounds like I found the problem!> **SeijiSensei said:**
> You can turn it on for the current session by running "echo '1' > /proc/sys/net/ipv4/ip_forward"It says it's not allowed/denied (I forget which sorry). I did use sudo.> **SeijiSensei said:**
> but to make the change permanent you need to edit /etc/sysctl.conf and enable the "net.ipv4.ip_forward=1" directive.I've done this, rebooted now "cat /proc/sys/net/ipv4/ip_forward" returns 1 :) It'll be tomorrow before I get a chance to check that all works as it should. Currently however, even connected to my local network I cannot ping any local machines. I think that may be connected to my next paragraph.

I'm afraid I didn't understand what you ment by your first paragraph. I don't think I've created any up script, network manager handles my connections.

Thanks for the idea so far, will report back tomorrow with more detailed responses.

---

### Post by Chrissd on 2011-06-15
Ok, I deleted the routing to 192.168.0.0 via the lan, since I won't always have a lan connection, but will always have a vpn connection. Why does it say the gateway is 10.8.0.5 when there is no 10.8.0.5 machine?

I now can't ping any 192.168.0.0 machines. 
```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        *               255.255.255.255 UH    0      0        0 tun0
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
192.168.0.0     10.8.0.5        255.255.255.0   UG    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by SeijiSensei on 2011-06-16
Let's see the contents of openvpn.conf, or whatever the .conf file you're using to set this up.  Use copy and paste with the [noparse][code][/noparse] tags, and give us the configuration files for both the client and server.

---

### Post by Chrissd on 2011-06-16
Server side.

```

#################################################
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

# Which local IP address should OpenVPN
# listen on? (optional)
local 192.168.0.3

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
;dev tap
dev tun

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
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh dh2048.pem

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

# Configure server mode for ethernet bridging
# using a DHCP-proxy, where clients talk
# to the OpenVPN server-side DHCP server
# to receive their IP address allocation
# and DNS server addresses.  You must first use
# your OS's bridging capability to bridge the TAP
# interface with the ethernet NIC interface.
# Note: this mode only works on clients (such as
# Windows), where the client-side TAP adapter is
# bound to a DHCP client.
;server-bridge

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
push "route 192.168.0.0 255.255.255.0"

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
# or bridge the TUN/TAP interface to the internet
# in order for this to work properly).
;push "redirect-gateway def1 bypass-dhcp"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
# The addresses below refer to the public
# DNS servers provided by opendns.com.
;push "dhcp-option DNS 208.67.222.222"
;push "dhcp-option DNS 208.67.220.220"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
;client-to-client

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
tls-auth ta.key 0 # This file is secret

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
user nobody
group nogroup

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
;log-append  openvpn.log

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

### Post by Chrissd on 2011-06-16
Client
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
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
;proto tcp
proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote 91.106.20.100 1194
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

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nogroup

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
ca /etc/openvpn/ca.crt
cert /etc/openvpn/NetBook.crt
key /etc/openvpn/NetBook.key

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
tls-auth /etc/openvpn/ta.key 1

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

---

### Post by SeijiSensei on 2011-06-17
OK, it appears that your using a setup that's designed to support multiple clients.  Is that what you need, or are you just trying to connect one client?  If the latter, I strongly recommend using a simple shared-key configuration as described in [this how-to]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  The configuration you're using is intended more for a "road-warrior" system with multiple computers connecting in remotely at the same time.

---

### Post by Chrissd on 2011-06-17
Hi, Thanks! That does look more simple. I now have

server.conf
```

dev tun
ifconfig 10.8.0.1 10.8.0.2
secret static.key
comp-lzo
keepalive 10 60
ping-timer-rem
persist-tun
persist-key
user nobody
group nobody
daemon

```

client.conf
```

remote myremote.mydomain
dev tun
ifconfig 10.8.0.2 10.8.0.1
secret static.key
comp-lzo
keepalive 10 60
ping-timer-rem
persist-tun
persist-key
user nobody
group nobody
daemon
route 192.168.0.0 255.255.255.0

```

What I don't get is this bit.
> Then on the server side, add a route to the server's LAN gateway that routes 10.8.0.2 to the OpenVPN server machine (only necessary if the OpenVPN server machine is not also the gateway for the server-side LAN).


What's that mean?

---

### Post by SeijiSensei on 2011-06-18
If OpenVPN is running on the same machine as that providing all other routes, then it should be possible to find machines in the 10.8.0.0/24 subnet without any further ado.  If, however, the machine that provides OpenVPN services is not also the central router, then additional routing needs to be added to the actual gateway.

Suppose, for instance, all the traffic on my local network resides in 192.168.0.0/24, and that network is connected to a NAT router that interconnects with the Internet.  Now suppose I have another machine with a publicly-visible IP address that acts as my OpenVPN server.  That server needs a route to the 192.168.0.0/24 network via the gateway to provide forwarding between the VPN hosts and the 192.168 network.

---

### Post by Chrissd on 2011-06-20
> **SeijiSensei said:**
> Suppose, for instance, all the traffic on my local network resides in 192.168.0.0/24, and that network is connected to a NAT router that interconnects with the Internet.  Now suppose I have another machine with a publicly-visible IP address that acts as my OpenVPN server.  That server needs a route to the 192.168.0.0/24 network via the gateway to provide forwarding between the VPN hosts and the 192.168 network.

This sounds like what I have. I have: 
```

                  (192.168.0.0 network)             (10.8.0.1)
Internet <-> Wireless Router <-> Server      <->    VPN Client
                             <-> Printer
                             <-> Other computers

```

So the printer and other computers are plugged into the same router. Do I add the router with something like
```

sudo route add -net 192.168.0.0 netmask 255.255.255.0

```?

Apologies but I'm only just understanding what this means. I understand it as two roads (networks) that run parrell, and I need to tell the people (data) that walk along these roads that there is a little path that connects it (the route). Without telling them there's a path, they won't realise it's there. That's probably very simplistic and I apologise for this.

Thanks for your help! :)

---

### Post by SeijiSensei on 2011-06-21
> **Chrissd said:**
> So the printer and other computers are plugged into the same router. Do I add the router with something like
```

sudo route add -net 192.168.0.0 netmask 255.255.255.0

```?

Typically you'd add the route on the client side and tell that machine to send traffic for 192.168 over the tunnel.  Suppose the client is 10.8.0.5 and the VPN server is 10.8.0.1.  Then the client would need a rule like:

```
sudo ip route add 192.168.0.0/24 via 10.8.0.1
```

That tells the client to send traffic intended for 192.168 over the tunnel but all other traffic is sent via the client's default gateway.

---

### Post by Chrissd on 2011-06-21
Hi,
Thanks! Ok, theory is understood, but now when I run
```
sudo /etc/init.d/openvpn restart
```

I get

```
 * Stopping virtual private network daemon(s)...                                 *   No VPN is running.
 * Starting virtual private network daemon(s)...                                 *   Autostarting VPN 'server'                                           [fail] 

```

Same happens client side, but obviously the client won't start since the server's not starting. I tried changing the path of secret to /etc/openvpn/static.key

Is there a way to see why it's not starting? Feel like I've taken a step forward and two backwards! Appreciate the help though!

---

### Post by spynappels on 2011-06-21
There is a possible issue with the subnet you have for your home LAN.

Your home LAN subnet is 192.168.0.0 with a subnet mask of 255.255.255.0 and this is an extremely common subnet, about half the small or home office routers come with this subnet preset. So imagine you are in a remote location and you connect to the net through WiFi, and the remote router gives you an IP of 192.168.0.165. You start up your VPN and it connects fine and pushes a route to your computer which says that all traffic for the 192.168.0.0 network needs to go through the VPN tunnel.

You now have a problem, as both the local and home LANs use the same subnet, and the computer does not know when you try to access a resource (such as a printer) at 192.168.0.50 (for example)whether you are trying to access that IP on the local LAN you are connected to or on your home LAN.

This is why I normally advise people who are starting with a home VPN setup to change their home subnet to something less common like 192.168.63.0 or whatever they want. This avoids routing conflicts. I don't know if this is feasible for you, but it may iron out a lot of headaches.

---

### Post by Chrissd on 2011-06-21
Insightful thoughts! Thanks!

Fortunately, there are two reasons why it's not an issue right now, but one I *will* address later. Firstly, most of other networks I connect to seem to use 192.168.1.0 IPs and secondly the VPN's not working right now, despite basically copying the example on the OpenVPN website.

---

### Post by spynappels on 2011-06-21
You had it working before, can you go back to that configuration, where you could ping the OpenVPN server. Can you go back to that config and we can look at getting the inter LAN routing working, if you like.

---

### Post by Chrissd on 2011-06-22
Woo! Went through it one line at a time! The fault lay with
```
group nobody

```
should have been
```
group nogroup

```!!!

Ok, I'm back and can ping the server! Have ```
route 192.168.0.0 255.255.255.0
```at the bottom
I tried ```
sudo ip route add 192.168.0.0/24 via 10.10.10.1
``` which returns ```
RTNETLINK answers: File exists
```

Route from a different network shows:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.1      *               255.255.255.255 UH    0      0        0 tun0
192.168.42.0    *               255.255.255.0   U     1      0        0 usb0
192.168.0.0     10.10.10.1      255.255.255.0   UG    0      0        0 tun0
default         192.168.42.129  0.0.0.0         UG    0      0        0 usb0

```

I can ping 10.10.10.1 but can't ping 192.168.0.11 (for example)

---

### Post by SeijiSensei on 2011-06-22
Perhaps IP forwarding is disabled on the OpenVPN server.  (It is disabled by default in Ubuntu.)  Take a look at /etc/sysctl.conf on the server and see if the line that sets "net.ipv4.ip_forward" to one is commented out.  If so, remove the comment, and reboot the server.  Can you ping the 192.168 network after doing that?

---

### Post by Chrissd on 2011-06-23
Hi,

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```
That's what I have, so it looks to me to be enabled.

---

### Post by spynappels on 2011-06-23
Chris, are you trying to connect to your VPN server from a remote location, or are the client and server on the same LAN (for testing)?

If you are connecting from inside the same LAN you will have the problems I spoke about earlier when your "local" and "remote" LANs have the same subnet.

---

### Post by Chrissd on 2011-06-23
Remote location. The BT Openzone network next door.

---

### Post by spynappels on 2011-06-23
Are you connecting from a Windows client or from a Linux client? I want to see what your routing table looks like but to show that depends on what platform you are using.

Linux (in terminal) route -e (may need sudo)
Windows (at command prompt) netstat -rn

---

### Post by Chrissd on 2011-06-23
Hi, actually this is what's causing the biggest problem for me with online help. Everyone refers to Windows clients. I'm all Ubuntu here.

sudo route -e
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.10.10.1      *               255.255.255.255 UH        0 0          0 tun0
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
192.168.0.0     10.10.10.1      255.255.255.0   UG        0 0          0 tun0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```

---

### Post by spynappels on 2011-06-23
Ok, so at least this tells us that the route is created correctly on the client.

What I'm pretty sure is happening is that the pings are getting to the "home" LAN resource ok, but the replies are getting lost as there is no route back to your client for them.

What you need to do now is set a return static route in your "home" LAN, for example you need to use a static route where all traffic for the 10.10.10.0 network is pushed back through the LAN IP (192.168.0.x) of your VPN server. 

This normally has to be done in your router, most allow you to set a static route. If you can tell me what router you have at home, I'll try and dig up some info on how to do that if you want.

---

### Post by Chrissd on 2011-06-23
A Netgear router, not sure of model. Has a "Static Route" button under the menu but not sure what to populate it with. Attached is what's in the relative frame under 'add'.

[img]http://img88.imageshack.us/img88/5382/staticroute.png[/img]

---

### Post by spynappels on 2011-06-23
Route Name = OpenVPN

Tick "Active"

Destination IP Address = 10.10.10.0
IP Subnet Mask = 255.255.255.0
Gateway IP Address = 192.168.0.x (LAN IP address of OpenVPN server)
Metric = 2

And then click Apply.

Let's see if that does the trick. You may need to reboot the router etc...

---

### Post by Chrissd on 2011-06-24
Hi,

Huge thanks! That worked! When I come home and connect to my home network again should I just delete the ip route and re add it when I leave? Is there a better way of doing that?

Is there anything else I should change when I change the third number later on and any restrictions tow what I change it to? Could I have 192.168.168.0?

Thanks again.

---

### Post by spynappels on 2011-06-24
> **Chrissd said:**
> Hi,

Huge thanks! That worked! When I come home and connect to my home network again should I just delete the ip route and re add it when I leave? Is there a better way of doing that?

Just leave the static route in place, it will only affect traffic coming from the VPN anyway. The route on the client should be automatically added when you connect to the VPN and removed when you disconnect, so you should be able to leave everything as it is and only connect to the VPN when you need to and it should all work fine.

> **Chrissd said:**
> 
Is there anything else I should change when I change the third number later on and any restrictions tow what I change it to? Could I have 192.168.168.0?

Thanks again.

That octet will be fine, just remember to change any static IPs to the new subnet and anywhere you entered an IP, like in the static route, so that everything is working on the same subnet. This is not too difficult in a small network as long as you are methodical and take one node at a time.

Glad you got it sorted.

---

### Post by Chrissd on 2011-06-24
Hi, thanks

There must be a better way to start and stop the VPN than the way I have it. My client boots and it's already running. I have to 'sudo /etc/init.d/openvpn stop'.

Network manager has a tick box for the VPN, but it doesn't actually do anything. Is there a better way than I do it, or just use an alias to control it?

Thanks again for your help so far!

---

### Post by spynappels on 2011-06-24
You can use Network Manager to control.your VPN connection on an ad-hoc basis, but I'll have to check the steps when I get home later.
It works very well and you can actually manage several different  connections at once.

---

### Post by spynappels on 2011-06-24
Ok, you can right click on the Network Manager icon in the notification area, and then click on Edit Connections.

Click on the VPN tab.

Click Import and select your client.conf file.

Give the connection a name, do not tick "Connect Automatically"

Put the public IP address or URL of the VPN server in the Gateway box.

Leave the Type set to TLS and in the other boxes put the path to the different certs and key.

Click on the Routes button in the IPv4 tab and tick the "Use this connection only for resources on its network"

Save the settings.

Now when you right click on the Network Manager and go down to VPN Connections, you should be able to click on the name you set to start the VPN connection. Quitting the VPN is pretty much the same but you click on Disconnect VPN instead.

---

### Post by Chrissd on 2011-06-25
Massive thanks once again! 

Can I just check if I need to add the "    route 192.168.4.0 255.255.255.0" or does it import that from the client.conf file?

---

### Post by spynappels on 2011-06-26
The route is normally pushed to the client from the server when you connect, so you should not have to worry about that.

---

### Post by Chrissd on 2011-06-27
Hi, 

For some reason Network manager isn't bringing to connection up and down. The box changes between ticked and unticked, but doesn't seem to do anything. ifconfig shows no tun connection and cannot ping 10.10.10.1. If I then do "sudo /etc/init.d/openvpn start" everything works normally.

Attached are screen shots of my Network Manger, apologies if they're in a strange order.

[img]http://img694.imageshack.us/img694/3518/vpn1.png[/img]

Under "Advanced" box.

[img]http://img691.imageshack.us/img691/3605/vpn3.png[/img]

[img]http://img839.imageshack.us/img839/504/vpn2.png[/img]

[img]http://img842.imageshack.us/img842/845/vpn4.png[/img]

Under "Routes" box.

[img]http://img833.imageshack.us/img833/8417/vpn5.png[/img]

---

### Post by spynappels on 2011-06-27
Ok, if you right click on the Network Manager Icon at the top of the screen and go down to VPN Connections, you should then be able to click on the connection you created to start that connection. When the connection is started, there will be a small padlock beside the Wireless ir wired connection icon.

To disconnect, right-click on the Network Manager icon again, go down to VPN connections and click on Disconnect VPN.

---

### Post by Chrissd on 2011-06-29
Ok, I found out why I thought it wasn't working:

When the PC boots, it starts with "/etc/init.d/openvpn start"ed. I have to "sudo /etc/init.d/openvpn stop" to stop it again. Anyway, using the above command to start OpenVPN, I get this
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.1      *               255.255.255.255 UH    0      0        0 tun0
192.168.168.0   10.10.10.1      255.255.255.0   UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

Network manager doesn't have the 192.168.168.0 route in there:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.1      *               255.255.255.255 UH    0      0        0 tun0
customer8234.po 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

It's in my client.conf, so I thought that would have been imported. 

Here's mytwo questions: 
I guess it's in the "routes" tab that I need to add it, but I'm not sure what I should add?

Secondly, how do I stop my PC from booting up with openvpn started? It's the command line that's starting with it, not the network manager, the box is definitely unticked.

Thanks again for all your help! It's been so helpful! You might notice I changed my networks IP following you advice! :)

---

### Post by Chrissd on 2011-07-04
Ok! I think I've solved this.

Firstly, to stop the VPN being loaded automatically, edit /etc/default/openvpn and uncomment the following line: ```
AUTOSTART=none
```

Next, I had to get my head around the there were two separate programs doing the same thing. This basically means that I had to fill in the table as said above, in network manager, configure VPN, and routes. Only box I didn't have a clue about was metric, so just left it blank. Hey presto, it works though!

Thanks for all the help! At least I might be able to help if someone is struggling setting up a VPN in future. 

I'll mark this as solved once I've rebooted and actually gone to university to test it out later this week.

---

