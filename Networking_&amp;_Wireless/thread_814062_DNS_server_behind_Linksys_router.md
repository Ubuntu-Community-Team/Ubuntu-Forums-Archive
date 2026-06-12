---
title: "DNS server behind Linksys router"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by billgarcia on 2008-05-31
Hi all,

My first post. I've followed the tutorials on setting up a DNS server using Ubuntu (my DNS is Xbuntu 8.04) and BIND9, located here:

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

My home setup is as follows:

Internet -> Linksys G Broadband Router -> (Computers)

All the machines on my network have been assigned private IP addresses, with the exception of those that connect to wireless, which is configured for DHCP.

I've set up my DNS forwarders to be the DNS servers of my ISP, and the DNS servers for my other computers all point to the private IP address of my DNS server (192.168.1.109, if you were wondering).

My router is configured to forward port 53 UDP/TCP to my DNS server. No other port forwarding is enabled. Also, my DNS server is also my Web server. As I understand it, I don't have to enable port forwarding for port 80 to my Web server. I actually want to run TWO web servers on my network. My ISP allows port forwarding to port 53, so I don't see any problem there.

Internally (that is, for any computer in my private network), the DNS server is running great. However, if I even try to visit any of the computers listed in my domain, I get timeout errors. Also, if I run an nslookup on any computer in my domain, I get its internal, private IP address. Here's my layout:

Computer name ; Private IP ; OS
assassin; 192.168.1.109; Xubuntu 8.04 (File/Web/DNS server)
nightcrawler; 192.168.1.104; Windows Vista Ultimate (Web server running on here, too)
wolverine; 192.168.1.105; Ubuntu 8.04
Vaio; 192.168.1.102; Windows XP Professional

I registered my domain name billgarcia.org with GoDaddy.com and changed my nameserver to my nameserver ns.billgarcia.org (with the public IP address of my router). So, my domain name is no longer hosted with GoDaddy and instead I've registered my DNS server with it (using the public IP of my router). Thus I've got ns.billgarcia.org as my nameserver for it, etc.

So my question is: What's the deal here? How come DNS works great from *inside* my network but I can't get to anything from *outside* the network? I've been working at this for a couple days and can't seem to get it to go. I've posted the code for all of my DNS config files below:

named.conf:

```
include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";

```

named.conf.local:

```
zone "billgarcia.org" {
        type master;
        file "/etc/bind/zones/billgarcia.org.db";
};

```

named.conf.options:

```
options {
        directory "/var/cache/bind";

        query-source address * port 53;

        forwarders {
                68.87.72.130;
                68.87.77.130;
        };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

and finally .../zones/billgarcia.org.db:

```
$TTL 3D
@ IN SOA ns.billgarcia.org. admin.billgarcia.org. (
        2007062001
        28800
        3600
        604800
        38400
);

billgarcia.org. IN      NS      ns.billgarcia.org.
billgarcia.org. IN      NS      ns2.billgarcia.org.
assassin        IN      A       192.168.1.109
ns              IN      A       192.168.1.109
ns              IN      A       192.168.1.109
www             IN      A       192.168.1.109
vaio            IN      A       192.168.1.102
gw              IN      A       192.168.1.1
wolverine	IN	A	192.168.1.105
nightcrawler	IN	A	192.168.1.104
			TXT	"Network Gateway"

```

---

### Post by jahservant on 2010-01-20
[http://en.wikipedia.org/wiki/Warnock's_Dilemma]("http://en.wikipedia.org/wiki/Warnock's_Dilemma")

---

### Post by ionisis on 2011-02-17
Not sure if this will help (a year later!). Maybe it'll help the next guy. I know that i went through hell over it...
 [http://forums.devshed.com/dns-36/dns-not-resolving-getting-servfail-after-4-days-788533.html](http://forums.devshed.com/dns-36/dns-not-resolving-getting-servfail-after-4-days-788533.html)
 
 @ Admins: i know, this is an old thread, but if you knew just how many  searches i did while trying to troubleshoot this problem, and how many  times i came across this thread, you'll understand that this thread  NEEDS an answer, for the visitor's sake, even if it is an old thread.  Hell, i don't even use Ubuntu (though i do recommend it to others (but  i'm a Fedora guy)). I just registered because i got tired of looking at this thread with no replies, which was 100% relevant...

---

