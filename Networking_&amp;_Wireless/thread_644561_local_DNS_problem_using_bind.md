---
title: "local DNS problem using bind"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by PowerBoardCable on 2007-12-19
Hi!
First of all - I'm new to this forum... hello to all :)

I have installed Ubuntu 7.10 (gutsy) on a box named "SomeServer". This box acts as Samba, Apache, MySQL server and hosts my intranet in my local network. There is no need to allow access from outside the LAN at this stage.

**What I want to do is this:**
Setting up a DNS on the same box that resolves the domain "someserver.com" and all subdomains - for the apache vhosts - to it's IP 192.168.1.102. This is supposed to be accessible and working for all computers in 192.168.1 range except 192.168.1.199 (which is the router).

**The Result and the problem:**
*After initial startup problems bind is now up and running. Unfortunately the domain is not found by ANY computer (including the server).*

Dig output:
```

root@SomeServer:~# dig someserver.com

; <<>> DiG 9.4.1-P1 <<>> someserver.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 5082
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;someserver.com.                IN      A

;; AUTHORITY SECTION:
com.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1198042644 1800 900 604800 900

;; Query time: 255 msec
;; SERVER: 211.29.132.12#53(211.29.132.12)
;; WHEN: Wed Dec 19 15:37:46 2007
;; MSG SIZE  rcvd: 113

```
211.29.132.12 is the IP of my ISP's DNS. Not sure, but I don't even think this should show up.

**What I did:**
As I have never worked with bind before and neither I'm a unix pro. - I changed the config files according to articles I found on this site and the rest of the internet.

my /etc/bind/named.conf (/etc/bind/named.conf.local is identical):
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
# This is the zone definition. replace example.com with your domain name
zone "SomeServer.com" {
        type master;
        file "/etc/bind/zones/SomeServer.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```

my /etc/bin/named.options:
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                211.29.132.12
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

my /etc/bind/zones/SomeServer.com.db:
```

SomeServer.com.      IN      SOA     ns1.SomeServer.com. admin.SomeServer.com. (
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

SomeServer.com.      IN      NS              ns1.SomeServer.com.
SomeServer.com.      IN      MX     10       mta.SomeServer.com.

www                                     IN      A       192.168.1.102
mta                                     IN      A       192.168.1.102
ns1                                     IN      A       192.168.1.102
*.SomeServer.com.                IN      A       192.168.1.102

```

my /etc/bind/zones/rev.1.168.192.in-addr.arpa:
```

@ IN SOA ns1.SomeServer.com. admin.SomeServer.com. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)
                     IN    NS     ns1.SomeServer.com.
1                    IN    PTR    SomeServer.com


```

my /etc/hosts:
```

#127.0.1.1	SomeServer
#127.0.1.1      SomeServer.com

127.0.0.1       localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I have also removed any reference in the XP host files to SomeServer.

Please help, I came so far and have the feeling the reason for this is something trivial that I've overlooked.

Thanks in advance,

Mike

---

### Post by PowerBoardCable on 2007-12-19
Hi all,

:oops: just saw that there is someone with exactly the same problem in this thread:
[http://ubuntuforums.org/showthread.php?t=644504](http://ubuntuforums.org/showthread.php?t=644504)

Should have searched the forum better - my apologies.

Mike

---

### Post by netztier on 2007-12-19
> **PowerBoardCable said:**
> 
211.29.132.12 is the IP of my ISP's DNS. Not sure, but I don't even think this should show up.


Well if you use dig just like that on your server, it's going to resolve that name according to the configuration found in /etc/nsswitch.conf and /etc/resolv.conf.

Especially if the latter of these still tells your local resolver to use your ISP's nameserver, you can expect to see your ISPs DNS here. You'd need to make sure that /etc/resolv.conf also refers to localhost or 127.0.0.1.

best regards

Marc

---

### Post by PowerBoardCable on 2007-12-19
Thanks a lot for your quick response!

changed, restarted and now getting this:
```

root@someserver:~# dig @localhost www.someserver.com

; <<>> DiG 9.4.1-P1 <<>> @localhost www.someserver.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38167
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;www.someserver.com.     IN      A

;; ANSWER SECTION:
www.someserver.com. 38400 IN     A       192.168.1.102

;; AUTHORITY SECTION:
someserver.com.  38400   IN      NS      ns1.someserver.com.

;; ADDITIONAL SECTION:
ns1.someserver.com. 38400 IN     A       192.168.1.102

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Dec 19 17:13:56 2007
;; MSG SIZE  rcvd: 93

root@someserver:~# dig @localhost 102.1.168.192

; <<>> DiG 9.4.1-P1 <<>> @localhost 102.1.168.192
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 41112
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;102.1.168.192.                 IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     A.ROOT-SERVERS.NET. NSTLD.VERISIGN-GRS.COM. 2007121801 1800 900 604800 86400

;; Query time: 200 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Dec 19 17:14:14 2007
;; MSG SIZE  rcvd: 106

```

But unfortunately it is still not resolving
I modified resolve.conf, it looks like this now:
```

nameserver 211.29.132.12
nameserver 127.0.0.1

```
... but i wouldn't know what to change in nsswitch:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

# hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
# modified as in http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4:
hosts:          files wins dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

The ISP's DNS IP is defined also as forwarder in /etc/bin/named.options. Do I actually need the ISP's DNS at all as I don't want the server to be accessible from outside the LAN??

Mike

---

### Post by netztier on 2007-12-19
> **PowerBoardCable said:**
> 
I modified resolve.conf, it looks like this now:
```

nameserver 211.29.132.12
nameserver 127.0.0.1

```


With this configuration, the server itself (i.e. when you use nslookup or dig on your server) will always ask your ISP's DNS first, and your ISP has no clue about SomeServer.com. 

The server's own name resolver (configured by /etc/resolv.conf)  is completely independent from the BIND that runs on it. This can lead to difficulties and misconceptions; therefore I suggest to configure the name resolver to use 127.0.0.1 as (first) DNS, then configure BIND to forward to your ISP (which you already did).

From what I understand, you want the PCs in your subnet to use the local DNS to resolve names. They will therefore send so-called recursive queries to the DNS [1] - so it's a good idea to define which clients are allowed to send recursive queries:


from /etc/bind/named.conf.options:
```
options {
        ..
        ..
        // By default, name servers should only perform recursive domain
        // lookups for their direct clients.  If recursion is left open
        // to the entire Internet, your name server could be used to
        // perform distributed denial of service attacks against other
        // innocent computers.  For more information on DDoS recursion:
        // http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987

[COLOR="Red"]        allow-recursion { 
            localnets; 
        };[/COLOR]
        ..
        ..
};
```

**dig**'s answers are sometimes a bit cryptic - I also use **nslookup ** (although it's old and often not recommended to use) to debug DNS.

> **PowerBoardCable said:**
> 
... but i wouldn't know what to change in nsswitch:


No one said you had to change it - it's just that it also plays a vital role in the name resolution process (in that it defines which resolution services are available and in what sequence they should be used) and should therefore be checked when analyzing name resolution problems.

regards

Marc


[SIZE="1"][1] recursive queries are sent by common "clients" to their DNS, and the DNS has to do the entire work by finding out which nameservers are authoritative for ".", then for "com.", then for "domain.com." then for "subdomain.domain.com." and then give the answer back to the client. 

A non-recursive query is just answered by ".com is what you want? Well, go ask nameserver xyz, it's authoritative for that!" - and you have to go and ask nameserver xyz yourself. The NS for .com will answer "domain.com is what you want? Well, go ask nameserver hkj, it's authoritative for that!" ... and so on.

By defining "forwarders", your local DNS will not do this recursive process itself, but will just ask your ISP's DNS to resolve it recursively.[/SIZE]

---

### Post by PowerBoardCable on 2007-12-19
One of these 2 settings made it work :)
After I added 192.168.1.102 as DNS for my XP machine it could resolve, subdomains get resolved, too.
Thanks so much for your help, much appreciated \\:D/
Thanks also for the explaining foot notes - helped me to understand the concept.

Mike

---

