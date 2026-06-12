---
title: "VPN/PPTP routing problem"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by Nobber on 2007-10-24
Any VPN/PPTP experts here?

I'm trying to connect to my work LAN from home using VPN, and while the connection appears to be successful, I can't see anything on the network once I'm connected. Even pinging the VPN server itself gets no response.

I followed the instructions [here](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand) to set up the pptp client, and this is what I see when connecting:

```
# pon acmecorp debug dump logfd 2 nodetach
...
<snip>
...
local  IP address 172.16.30.129
remote IP address W.X.Y.Z
Script /etc/ppp/ip-up started (pid 5685)
Script /etc/ppp/ip-up finished (pid 5685), status = 0x0
```

where W.X.Y.Z is the public IP address of the VPN server. Unfortunately this sets up a so-called [IP loop](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data), which I fix using option 4b in that previous link (i.e. change the point-to-point IP address of the ppp0 interface to the internal address of the VPN server):

```
ifconfig ppp0 pointopoint 172.16.31.1
```

Then my routing table looks like this:

```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.31.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 ath0
```

Which apparently gives me no route to the 172.16.0.0 network, so I add one:

```
# route add -net 172.16.0.0/16 dev ppp0
```

But still no joy, no successful pings.

Since I am apparently connecting successfully, I assume the problem is just down to routing. But how should the routing be set up? For reference, the routing table on a Windows client that has successfully connected to the VPN server (over the wireless network at work) looks like this:

```
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1   192.168.1.117   25
          W.X.Y.Z  255.255.255.255      192.168.1.1   192.168.1.117   25
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1   1
       172.16.0.0      255.255.0.0    172.16.30.130   172.16.30.130   1
    172.16.30.130  255.255.255.255        127.0.0.1       127.0.0.1   50
   172.16.255.255  255.255.255.255    172.16.30.130   172.16.30.130   50
      192.168.1.0    255.255.255.0    192.168.1.117   192.168.1.117   25
    192.168.1.117  255.255.255.255        127.0.0.1       127.0.0.1   25
    192.168.1.255  255.255.255.255    192.168.1.117   192.168.1.117   25
        224.0.0.0        240.0.0.0    172.16.30.130   172.16.30.130   50
        224.0.0.0        240.0.0.0    192.168.1.117   192.168.1.117   25
  255.255.255.255  255.255.255.255    172.16.30.130               2   1
  255.255.255.255  255.255.255.255    172.16.30.130   172.16.30.130   1
  255.255.255.255  255.255.255.255    192.168.1.117   192.168.1.117   1
Default Gateway:       192.168.1.1
```

where 172.16.30.130 is the IP address assigned on the VPN. What a mess.

Help!

---

