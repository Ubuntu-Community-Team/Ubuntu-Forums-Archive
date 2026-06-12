---
title: "OpenVPN: Can't start tun0 on client"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by Mar Komus on 2014-06-10
Newbie at OpenVPN and started following the guide found [here]("https://help.ubuntu.com/14.04/serverguide/openvpn.html"). I got as far as, "Now start the OpenVPN client." I typed the command, "service openvpn start." Upon checking with "ifconfig tun0" to verify that it started, I received the following message:

> tun0: error fetching interface information: Device not found



What'd I do wrong? :(

[Note: I've followed this tutorial several times on different clients with the same results]

[Note: I'm NOT running Natty Narwhal. All my machines are 14.04]

---

### Post by kira_belka2 on 2014-06-11
ps ax | grep openvpn

and cat /etc/openvpn/openvpn.conf plz

---

### Post by SeijiSensei on 2014-06-11
I always specify 
```
dev tun
```
in my OpenVPN configuration files.  I looked briefly at that help page you cited and don't see any suggestions to include a device line.  Give that a try.

---

### Post by Mar Komus on 2014-06-11
In order of appearance:

kira_belka2: Here are the returns for those commands, respectively:

>  1085 ?        Ss     0:00 /usr/sbin/openvpn --writepid /run/openvpn/client.pid --daemon ovpn-client --status /run/openvpn/client.status 10 --cd /etc/openvpn --config /etc/openvpn/client.conf --script-security 2 1943 pts/12   R+     0:00 grep --color=auto openvpn

> cat: /etc/openvpn/openvpn.conf: No such file or directory

For the second, do you mean for me to perform that operation on the *client.conf* file? If so, here is the output:

> ##############################################
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
remote {*server name redacted*} 1194
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
ca ca.crt
cert markomus.crt
key markomus.key


# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm)
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


SeijiSensei: *dev tun* appears in my *client.conf* file. Is that what you mean, or should it also appear somewhere else?

---

### Post by Mar Komus on 2014-06-11
Here's some more information I pulled from the *syslog* on the client:

> Jun 11 14:40:27 Laptop1 ovpn-client[1065]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)Jun 11 14:40:27 Laptop1 ovpn-client[1065]: TLS Error: TLS handshake failed
Jun 11 14:40:27 Laptop1 ovpn-client[1065]: SIGUSR1[soft,tls-error] received, process restarting
Jun 11 14:40:27 Laptop1 ovpn-client[1065]: Restart pause, 2 second(s)
Jun 11 14:40:29 Laptop1 ovpn-client[1065]: Socket Buffers: R=[212992->131072] S=[212992->131072]
Jun 11 14:40:29 Laptop1 ovpn-client[1065]: UDPv4 link local: [undef]
Jun 11 14:40:29 Laptop1 ovpn-client[1065]: UDPv4 link remote: [AF_INET]{*IP address redacted*}:1194


---

### Post by Mar Komus on 2014-06-11
Bingo. I figured it out. Port Forwarding rule was incorrect. I had it set as "UDP 1194 -> 1194." Looking at the other rules, I noticed the default ones all said something like, "Any -> {*port number*}." I was fooled, though, because there were other entries that said, "{*port number*} -> {*port number*}." But at any rate, I made the change just to see what would happen and whaddaya know? We're in business.

Thanks for your help!

---

