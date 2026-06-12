---
title: "Problems using cisco anyconnect client and openconnect"
date: 2013-10-19
forum: Networking &amp; Wireless
---

### Post by maik2 on 2013-10-19
Hi there,

my university (University of Tuebingen, Germany) has recently changed from vpnc to cisco anyconnect, which doesn't seem to work for me at all.

Using 12.10 I have installed both the Cisco anyconnect and the Openconnect compatible client. I can log on with no problems but 9 out of 10 times the connection gets so slow that I can't go to any website. Typically, I get a "ntpdate[]: no server suitable for synchronization found". Please see full syslog of a test session below. Here, I was trying to go to a perfectly normal website ([http://www.ncbi.nlm.nih.gov/pubmed/](http://www.ncbi.nlm.nih.gov/pubmed/)) but firefox got stuck "connecting". I logged out after several minutes because nothing happend at all. 

Strangely enough, in some rare cases, everything seems to work fine and I can work at a perfectly normal speed for at least several minutes. No idea what I might be doing differently there.

Can anybody help?

Cheers,

Maik

Oct 19 17:06:19 mce-laptop NetworkManager[949]: <info> Starting VPN service 'openconnect'...
Oct 19 17:06:19 mce-laptop NetworkManager[949]: <info> VPN service 'openconnect' started (org.freedesktop.NetworkManager.openconnect), PID 16351
Oct 19 17:06:19 mce-laptop NetworkManager[949]: <info> VPN service 'openconnect' appeared; activating connections
Oct 19 17:06:26 mce-laptop NetworkManager[949]: <info> VPN plugin state changed: starting (3)
Oct 19 17:06:26 mce-laptop NetworkManager[949]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vpn0, iface: vpn0)
Oct 19 17:06:26 mce-laptop NetworkManager[949]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vpn0, iface: vpn0): no ifupdown configuration found.
Oct 19 17:06:26 mce-laptop NetworkManager[949]: <warn> /sys/devices/virtual/net/vpn0: couldn't determine device driver; ignoring...
Oct 19 17:06:26 mce-laptop NetworkManager[949]: <info> VPN connection 'Uni Tübingen' (Connect) reply received.
Oct 19 17:06:26 mce-laptop openconnect[16363]: Attempting to connect to 193.197.62.141:443
Oct 19 17:06:26 mce-laptop openconnect[16363]: SSL negotiation with ras1.uni-tuebingen.de
Oct 19 17:06:27 mce-laptop openconnect[16363]: Connected to HTTPS on ras1.uni-tuebingen.de
Oct 19 17:06:27 mce-laptop openconnect[16363]: Got CONNECT response: HTTP/1.1 200 OK
Oct 19 17:06:27 mce-laptop openconnect[16363]: CSTP connected. DPD 30, Keepalive 20
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info> VPN connection 'Uni Tübingen' (IP Config Get) reply received.
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info> VPN connection 'Uni Tübingen' (IP4 Config Get) reply received.
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info> VPN Gateway: 193.197.62.141
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info> Tunnel Device: vpn0
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info> IPv4 configuration:
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Internal Address: 134.2.219.50
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Internal Prefix: 23
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Internal Point-to-Point Address: 134.2.219.50
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Maximum Segment Size (MSS): 0
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Forbid Default Route: no
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Internal DNS: 134.2.200.1
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   Internal DNS: 134.2.200.2
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info>   DNS Domain: 'uni-tuebingen.de'
Oct 19 17:06:27 mce-laptop NetworkManager[949]: <info> No IPv6 configuration
Oct 19 17:06:27 mce-laptop openconnect[16363]: Connected vpn0 as 134.2.219.50, using SSL
Oct 19 17:06:27 mce-laptop openconnect[16363]: Established DTLS connection (using OpenSSL)
Oct 19 17:06:28 mce-laptop NetworkManager[949]: <info> VPN connection 'Uni Tübingen' (IP Config Get) complete.
Oct 19 17:06:28 mce-laptop acvpnagent[1158]: A new network interface has been detected.
Oct 19 17:06:28 mce-laptop acvpnagent[1158]: Function: logInterfaces File: ../../vpn/AgentUtilities/Routing/InterfaceRouteMonitorCommon.cpp Line: 477 IP Address Interface List: 192.168.2.101 134.2.219.50 FE80:0:0:0:2E81:58FF:FEF8:6C2 
Oct 19 17:06:28 mce-laptop NetworkManager[949]: <info> Policy set 'Uni Tübingen' (vpn0) as default for IPv4 routing and DNS.
Oct 19 17:06:28 mce-laptop NetworkManager[949]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Oct 19 17:06:28 mce-laptop dnsmasq[2312]: setting upstream servers from DBus
Oct 19 17:06:28 mce-laptop dnsmasq[2312]: using nameserver 134.2.200.2#53
Oct 19 17:06:28 mce-laptop dnsmasq[2312]: using nameserver 134.2.200.1#53
Oct 19 17:06:29 mce-laptop dbus[617]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 19 17:06:29 mce-laptop NetworkManager[949]: <info> VPN plugin state changed: started (4)
Oct 19 17:06:29 mce-laptop NetworkManager[949]:    keyfile: updating /etc/NetworkManager/system-connections/Uni Tübingen
Oct 19 17:06:29 mce-laptop dbus[617]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 19 17:06:38 mce-laptop ntpdate[16455]: no server suitable for synchronization found
Oct 19 17:07:57 mce-laptop openconnect[16363]: DTLS Dead Peer Detection detected dead peer!
Oct 19 17:07:57 mce-laptop openconnect[16363]: Established DTLS connection (using OpenSSL)
Oct 19 17:10:04 mce-laptop openconnect[16363]: DTLS Dead Peer Detection detected dead peer!
Oct 19 17:10:04 mce-laptop openconnect[16363]: Established DTLS connection (using OpenSSL)

---

### Post by rijidij on 2013-10-21
I'm definitely not a VPN expert, but you might want to set up split tunneling.
Edit your VPN connection and go to the IPv4 Settings tab.
Click the Advanced... button, then check the "Use this connection only for resources on its network" checkbox.
Save your changes.
Now your internet browsing will not be routed through the VPN but you should still be able to access its resources.

HTH

---

### Post by maik2 on 2013-10-22
When I do this I can browse the net at normal speed but don't have access to secured resources (normally available through the uni net) anymore.

Maik

---

