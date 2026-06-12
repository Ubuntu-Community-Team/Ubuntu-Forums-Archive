---
title: "OpenVPN client and server in VirtualBox"
date: 2018-01-04
forum: Networking &amp; Wireless
---

### Post by miniKOX on 2018-01-04
Hello.

I do not know if this this forum is right place for such problems, but I will describe it.

I have got 2 virtual machines installed(in Virtual Box, which is working on physical computer with Windows 8). 

Both virtual machines are with Ubuntu 16.04 installed on it.

My task is to install OpenVPN server on one virtual machine and OpenVPN client on the second virtual machine, which I have already done, and to make them communicate(pinging) each other(which I have not done, for I do not realize why the communication does not work).

So now I have got these 2 virtual machines, but none of them is able to communicate with each other. Both VM are connected to my home network, but on client VM, when I type the VPN-server's IP, client cannot reach it.

Can someone tell me where is the problem, what am I doing bad and what to do to make it work?

Here I give configuration file listings for server and client.


Server:

```

port 1194
proto udp
dev tun0

ifconfig [172.16.1.1]("https://l.facebook.com/l.php?u=http%3A%2F%2F172.16.1.1%2F&h=ATPIGLh3D9BmYRg5wfQacmi5KymwS283nvT_Pm8pBBscOESQHy7ip4X_qZz81iz7Ryn-s6lExbDNhvHQ8OgxBSs4YCQZDZdcQukbFZsqKmDzFvdh0cIDbqW4KAdXDlCXBFmqbH-qUOl0") [172.16.1.20]("https://l.facebook.com/l.php?u=http%3A%2F%2F172.16.1.20%2F&h=ATPIGLh3D9BmYRg5wfQacmi5KymwS283nvT_Pm8pBBscOESQHy7ip4X_qZz81iz7Ryn-s6lExbDNhvHQ8OgxBSs4YCQZDZdcQukbFZsqKmDzFvdh0cIDbqW4KAdXDlCXBFmqbH-qUOl0")

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem

server [10.8.0.0]("https://l.facebook.com/l.php?u=http%3A%2F%2F10.8.0.0%2F&h=ATPIGLh3D9BmYRg5wfQacmi5KymwS283nvT_Pm8pBBscOESQHy7ip4X_qZz81iz7Ryn-s6lExbDNhvHQ8OgxBSs4YCQZDZdcQukbFZsqKmDzFvdh0cIDbqW4KAdXDlCXBFmqbH-qUOl0") [255.255.255.0]("https://l.facebook.com/l.php?u=http%3A%2F%2F255.255.255.0%2F&h=ATPIGLh3D9BmYRg5wfQacmi5KymwS283nvT_Pm8pBBscOESQHy7ip4X_qZz81iz7Ryn-s6lExbDNhvHQ8OgxBSs4YCQZDZdcQukbFZsqKmDzFvdh0cIDbqW4KAdXDlCXBFmqbH-qUOl0")

ifconfig-pool-persist ipp.txt


push "redirect-gateway"
push "dhcp-option DNS 10.8.0.1"
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn-status.log
log /var/log/openvpn.log
verb 3







```

and for client(on second VM):

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
remote [10.8.0.0]("https://l.facebook.com/l.php?u=http%3A%2F%2F10.8.0.0%2F&h=ATPIGLh3D9BmYRg5wfQacmi5KymwS283nvT_Pm8pBBscOESQHy7ip4X_qZz81iz7Ryn-s6lExbDNhvHQ8OgxBSs4YCQZDZdcQukbFZsqKmDzFvdh0cIDbqW4KAdXDlCXBFmqbH-qUOl0") 1194


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
user nobody
group nogroup

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
#ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/client1.crt
key /etc/openvpn/easy-rsa/keys//client1.key
# Verify server certificate by checking that the
# certicate has the correct key usage set.
# This is an important precaution to protect against
# a potential attack discussed here:
#  [http://openvpn.net/howto.html#mitm]("https://l.facebook.com/l.php?u=http%3A%2F%2Fopenvpn.net%2Fhowto.html%23mitm&h=ATPIGLh3D9BmYRg5wfQacmi5KymwS283nvT_Pm8pBBscOESQHy7ip4X_qZz81iz7Ryn-s6lExbDNhvHQ8OgxBSs4YCQZDZdcQukbFZsqKmDzFvdh0cIDbqW4KAdXDlCXBFmqbH-qUOl0")
#
# To use this feature, you will need to generate
# your server certificates with the keyUsage set to
#   digitalSignature, keyEncipherment
# and the extendedKeyUsage to
#   serverAuth
# EasyRSA can do this for you.
remote-cert-tls server

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

I tried to ping from client to server and from server to client with addresses:
172.16.1.1
172.16.1.20
10.8.0.0
10.8.0.1

but only 10.8.0.1 works, and only on VM which works as a server.

As for "Networking" of my virtual machines(such panel in Virtual Box): both of them are working in NAT, i also tried "bridged" but no success in pinging.

Can someone help me with this? Thank You in advance for your help.

---

### Post by TheFu on 2018-01-04
Are both VMs configured to use bridge networking, not NAT?
If both VMs can't ping each other, then you shouldn't bother trying anything else.

---

### Post by miniKOX on 2018-01-04
Thank You for your reply.

I tried:

NAT-NAT
NAT-bridge
bridge-NAT
bridge-bridge

and isolated network also.

---

### Post by TheFu on 2018-01-04
If bridge isn't working then you have bigger issues.  NAT won't work without manual port forwarding.  I don't use NAT except for toy VMs.

Go with bridged, setup the static IPs on the same network as the host (this is done inside each VM guest), and ping away. If some other machine on the network can ping the VM guests, things should work.

BTW, disable any vpn.

---

