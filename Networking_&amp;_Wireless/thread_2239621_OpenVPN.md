---
title: "OpenVPN"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by Saicho on 2014-08-14
I'd like a VPN server setup on my home network so a remote machine can access content on my LAN as well as be able to "proxy" all of the remote machine's internet traffic through my home network (to overcome a Strict NAT where the remote machine is located). My home network looks like this:

Cable Modem
Wireless Router (old-ish, not DD-WRT capable, running a DHCP server for 192.1.x.x with some reservations)
Machine running 12.04 LTS with 1 physical ethernet port connected to the router via a switch (tons of other machines on the LAN as well)

I assume to achieve this I need to setup OpenVPN in bridged mode? I'm not very well versed in ethernet bridges or VPNs in general. I've read some OpenVPN on Ubuntu guides out there but I don't think they exactly cover my use-case. Is there a particular guide I should be following that will show me how to setup OpenVPN to do what I want?

Thanks in advance!

-Saicho

---

### Post by weatherman2 on 2014-08-14
I've setup OpenVPN as you describe on several Ubuntu 12.04 servers.

This guide is close to what I did:

[http://ubuntuguide.org/wiki/OpenVPN_server](http://ubuntuguide.org/wiki/OpenVPN_server)

I did use bridging.  This is my generic /etc/network/interfaces file (avoids having a static IP set on the server itself):

```

auto eth0
iface eth0 inet manual
up ip link set $IFACE up promisc on

auto br0
iface br0 inet dhcp


bridge_ports eth0


auto lo
iface lo inet loopback

```

This is my server.conf file in /etc/openvpn/  . I don't suggest you use it - I suggest you use it as reference if you are having trouble getting yours to work.  (I have a password auth script I edited out as well.)

```

port 1194
proto udp


dev tap0


# script to attach the tap0 interface to the bridge
up "/etc/openvpn/up.sh br0 1500"
down "/etc/openvpn/down.sh br0"


ca ca.crt


#Public Client Cert aka Public Server Cert
cert cert.pem


#Private  Client Key aka Private Server Key
key key.pem  # This file should be kept secret


tls-auth ta.key 0 # This file is secret


dh dh.pem

# Only require ta.key and and ca.crt
# Less secure (I was also using password auth with this)
client-cert-not-required

tmp-dir /dev/shm
script-security 3
username-as-common-name

# optional username/password check in addition to certificates
# you need to use your own password-check.sh script here (I am declining to share mine)
#auth-user-pass-verify /etc/openvpn/password-check.sh  via-file


#assume my local network is on 192.168.0.1/24 and that 
# OPENVPN SERVER can assign IPs from 192.168.0.240  to 192.168.0.249 
# make sure your router doesn't assign IPs in this space!
server-bridge 192.168.0.1 255.255.255.0 192.168.0.240 192.168.0.249


push "route 192.168.0.0 255.255.255.0"


# You may want this to redirect traffic through the VPN
# I have disabled it, not sure if you will need it, may depend on your client
#push "redirect-gateway def1 bypass-dhcp"

#use my router's DNS so I get the local name server on my network to resolve 
# local IP of local machines
push "dhcp-option DNS 192.168.0.1"


client-to-client


#one shared set of certificates by all clients
#less secure for sure if using multiple users - but easier to manage, only one set of certificates 
#needed for multiple logins/multiple users
duplicate-cn


keepalive 10 120


user nobody
group nogroup


persist-key
persist-tun


status openvpn-status.log


log-append  openvpn.log


verb 3

```

---

### Post by weatherman2 on 2014-08-14
I'll also add that I also have OpenVPN running on TomatoUSB routers that have enough memory to run the full version with an OpenVPN sever. It is much easier to do it this way.  (TomatoUSB is an alternative firmware to DD-WRT.)  A TomatoUSB-capable router may be cheaper to buy used than you might think.

Either way, you still need to generate some certificates using the guide I linked to above.

---

### Post by Saicho on 2014-08-15
Thanks for the quick reply!

I'm having problems with this. The first thing I tried to do was create the bridge and restart to see what happened. I edited /etc/network/interfaces to what you pasted above. After a restart I got a "Waiting for network connection" message. I had to revert back to my original file to get networking working again. Here is what my working /etc/network/interfaces looks like right now:

```

auto lo
iface lo inet loopback
```

I have a pretty good idea of what to do after the bridge is setup, but at the moment I'm still stuck :mad:

---

### Post by weatherman2 on 2014-08-15
Sorry, should have clarified: you need to create the bridge br0 so that my interfaces file will work.

My OpenVPN server.conf file posted above contains two script calls that create and remove the bridge; "up" is run when the server is running, I believe:

```

up "/etc/openvpn/up.sh br0 1500"
down "/etc/openvpn/down.sh br0"

```

You need to install the Bridge Control tools:

```

sudo apt-get update
sudo apt-get install bridge-utils

```

You should find the up.sh and down.sh scripts in your /etc/openvpn/ directory - but if not, here are mine:

up.sh:

```

#!/bin/sh


BR=$1
ETHDEV=$2
TAPDEV=$3


/sbin/ip link set "$TAPDEV" up
/sbin/ip link set "$ETHDEV" promisc on
/sbin/brctl addif $BR $TAPDEV

```




down.sh:

```

#!/bin/sh


BR=$1
DEV=$2


/sbin/brctl delif $BR $DEV
/sbin/ip link set "$DEV" down

```

---

