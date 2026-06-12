---
title: "is vpn working fine?"
date: 2017-11-14
forum: Networking &amp; Wireless
---

### Post by zhanglini on 2017-11-14
I have set up my ovpn and the following is the result of "ifconfig":
1. I know lo is local loop; tun0 is my vpn; but what are enp3s0 and wlxe0915334d414 (which has more traffic than tun0, 1.2G vs 1.1G)
2. is "wlxe0915334d414" leaking my identity?
Thanks
```
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether aa:bb:cc:dd:ee:ff  txqueuelen 1000  (&#20197;&#22826;&#32593;)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (&#26412;&#22320;&#29615;&#22238;)
        RX packets 5111  bytes 427330 (427.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5111  bytes 427330 (427.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet aa.bb.cc.dd  netmask 255.255.255.255  destination 10.211.1.38
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (&#26410;&#25351;&#23450;)
        RX packets 902429  bytes 1137903098 (1.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 291925  bytes 20401741 (20.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlxe0915334d414: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.2  netmask 255.255.255.0  broadcast 192.168.0.255
        ether e0:91:53:34:d4:14  txqueuelen 1000  (&#20197;&#22826;&#32593;)
        RX packets 912014  bytes 1225262124 (1.2 GB)
        RX errors 0  dropped 16852  overruns 0  frame 0
        TX packets 292504  bytes 55227510 (55.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### Post by 1clue on 2017-11-14
enp3s0 is your ethernet card.

wlxewhatever is likely your wireless interface, whatever physical device you use to activate your tunnel. enp3s0 has zero bytes through it so your tun0 is over the wlxe interface.

By necessity the physical interface the tunnel goes over has more traffic than the tunnel itself.

While I'm no expert at trying to cover my tracks, I know that being truly anonymous on the Internet is extremely difficult.

---

### Post by 1clue on 2017-11-14
Getting back to the point,

Surely some traffic goes through the nic without being in the tunnel. There is handshaking to set up the tunnel, and there is traffic to keep your connection to your isp running for example.

There's also the issue that your VPN may be configured to only reroute traffic to a specific subnet. My openvpn setup only reroutes traffic to the LAN that contains the vpn device, allowing all other traffic to go through whatever ISP the vpn client is using.

---

### Post by zhanglini on 2017-11-14
Thanks!  I understand every word you are using, but still bit confused any ways.  This network thing drives me crazy.

---

### Post by 1clue on 2017-11-14
What is it that drives you crazy?

You have a VPN to somewhere, but in order to get to that "somewhere" you need a regular TCP/IP connection. So your network device needs to send traffic to your router, do some dns lookups, whatever it takes. That's all traffic outside of the tunnel. Then it needs to negotiate with the tunnel endpoint, which as I understand it is also outside of the tunnel. Once a connection is established, some or all of your traffic will go through the tunnel. Moreover, some traffic might go to your local printer which would be through wlxe* but not through the tunnel. Some might go to your other local computers, a NAS, or whatever.

Whether traffic continues to flow through wlxesomething after your tunnel is in place I don't know. But you could find out by leaving your tunnel up, generate a bunch of traffic and see if your traffic "gap" between wlxe* and tun0 remains the same number of bytes or if it grows.

Whether the wlxe* traffic leaked your identity depends on what went through that wire outside of the tunnel, and what went through the tunnel. FWIW if the vpn endpoint is monitored by somebody you consider to be a hostile entity then you'd just as well not have a vpn.

Remember that with encryption, you need to consider all the potential players. Who do you trust?  How much do you trust them?  Whose territory do you cross to get to the guy you trust?  How much might they want to know what you're sending? How careful were you when setting all this up?  How much do you really know about keeping secrets?  How much do the people you trust know? Who doesn't like you? Who doesn't like the people you trust? Who wrote the software you use? Who developed the encryption algorithm you used? Has that algorithm been compromised?  That's all from like 2 minutes of thinking. There are a lot more questions to ask in the same vein. Most of the answers aren't yes/no, nor are they a greyscale but an entire color wheel.

I suspect that if you really want answers about what's going through the wire you'll need to monitor your ethernet port with something like wireshark and maybe a few more tools. A managed switch really helps with that, especially if you're only interested in Internet traffic.

---

### Post by zhanglini on 2017-11-15
thanks for clearing up :)

---

