---
title: "Routing for a 12 interface ftp server - downloading problem"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by mediaeast on 2007-05-08
I have proFTPd setup on an Ubuntu server with 12 network interfaces, each one connected to a separate DSL line. The server binds to the 12 interfaces fine but has trouble taking connections on the 11 other than the first interface.

- Each DSL line has a dynamic IP and is mapped to a DynDNS name.
- Each interface is behind a NAT in the DSL router. (An incoming connection is able to get to the server so the incoming NAT is working fine)
- All relevant ports are opened for FTP on each router and forwarded to the appropriate internal IP
- Each interface in proFTPd is setup to use a DNS service to lookup the interface IP for PASV transfers. Each interface has a different DNS name
- All interfaces are visible and enabled in the interface list
- Each of the interfaces has an internal IP of 192.168.n.11 and the router has an IP of 192.168.n.1.
- The server is running Ubuntu Server 6.10 with no firewall software

With these routes I was able to ftp to each interface independently and get directory listings. I am also able to upload data from the client to each of the 12 interfaces.

ip route add 192.168.2.0/24 dev eth2 src 192.168.2.11 table r2
ip route add 192.168.3.0/24 dev eth3 src 192.168.3.11 table r3
...
ip route add 192.168.12.0/24 dev eth12 src 192.168.12.11 table r12

ip rule add from 192.168.2.11 table r2
ip rule add from 192.168.3.11 table r3
...
ip rule add from 192.168.12.11 table r12

ip route add default via 192.168.2.1 table r2
ip route add default via 192.168.3.1 table r3
...
ip route add default via 192.168.12.1 table r12

The strange part is that I am actually able to download in ascii mode but not in binary mode from any of the interfaces other than the default interface (eth1)

I also tried loading ip_conntrack and ip_conntrack_ftp but that did not work. I also added the following iptable entries but they didn't help either.

iptables -A INPUT -i eth2 -p tcp --sport 1024: --dport 1024:  -d 192.168.2.11 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o eth2 -p tcp --sport 1024: --dport 1024:  -s 192.168.2.11 -m state --state ESTABLISHED -j ACCEPT

So now I am able to do the following using PASSIVE mode
- Upload from Client -> Server in ASCII and BINARY mode
- Download from Server -> Client in ASCII mode only.

I have also tried several ftp clients.

Any ideas why BINARY mode is not working for downloads?

Thanks

---

### Post by mediaeast on 2007-05-12
Any routing or ftp experts out there who can help with this problem? 

Your advice will be greatly appreciated.

Thanks in advance,

Mediaeast

---

### Post by mediaeast on 2007-06-21
I have run Wireshark to trace the packets during the ftp sessions and there does not seem to be any significant differnce between the way the ftp daemon is handling ASCII vs BINARY transfers. They both seem to follow an almost identical pattern.

Does ny one have any ideas why outgoing transfers would only work in ASCII mode but not in BINARY mode? Incoming transfers work in both modes. All FTP data exchange takes place in passive mode becuase I am behind a NAT for each interface.

Basically, is there any routing setting that could be causing this discrepancy?

I have tried ip_conntrack and ip_conntrack_ftp. I also have individual routing tables for each interface. Each interface has its own default route and then there is one global default route for eth0/first interface.

On this first interface all traffic is fine and I am able to ftp in and out in all modes correcty. Only the interfaces that are higher than this one have a problem.

Thanks

---

