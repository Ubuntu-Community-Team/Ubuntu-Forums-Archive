---
title: "DNS server causing slow connection"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by jazzguitarplayer on 2008-04-03
Hello guys,

I'm new to Linux so maybe you could help me out. I installed a DNS server with bind to learn about how DNS works in Linux  (not for permanent use) .  If I browse through the internet my connection is very slow. For each website i have to wait at least 5 seconds. When I use Proftpd (ftp server) it's slow as well. If I use my draytek router as  DNS server the internet browsing and proftpd works alot faster. So how do i have to adjust my configuration file to speed up this. Here is my default DNS configuration file..


  GNU nano 2.0.6              File: /etc/hosts                                 



127.0.0.1 localhost

192.168.1.12 linux-computer



# The following lines are desirable for IPv6 capable hosts

::1 ip6-localhost ip6-loopback

fe00::0 ip6-localnet

ff00::0 ip6-mcastprefix

ff02::1 ip6-allnodes

ff02::2 ip6-allrouters

ff02::3 ip6-allhosts

192.168.1.11 black



DNS record:



// This is the primary configuration file for the BIND DNS server named.

//

// Please read /usr/share/doc/bind9/README.Debian.gz for information on the

// structure of BIND configuration files in Debian, *BEFORE* you customize

// this configuration file.

//

// If you are just adding zones, please do that in /etc/bind/named.conf.local



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



// zone "com" { type delegation-only; };

// zone "net" { type delegation-only; };



// From the release notes:

//  Because many of our users are uncomfortable receiving undelegated answers

//  from root or top level domains, other than a few for whom that behaviour

//  has been trusted and expected for quite some length of time, we have now

//  introduced the "root-delegations-only" feature which applies delegation-only

//  logic to all top level domains, and to the root domain.  An exception list

//  should be specified, including "MUSEUM" and "DE", and any other top level

//  domains from whom undelegated responses are expected and trusted.

---

### Post by Eiríkr on 2008-04-03
Your symptoms sound very much like your DNS server setup has failed, and your hostname resolution attempts wait a while for a response from your local server before attempting the backup server (likely your ISP's).  

Try looking in your syslog for any messages from the named daemon:
```
grep named /var/log/syslog
```

Cheers,

Eiríkr

---

### Post by jazzguitarplayer on 2008-04-04
thanks for your reply. THis is what i get:

root@linux-computer:~# grep named /var/log/syslog
Apr  4 01:29:16 linux-computer named[5110]: listening on IPv4 interface vmnet1, 172.16.150.1#53
Apr  4 01:29:16 linux-computer named[5110]: listening on IPv4 interface vmnet8, 192.168.150.1#53

What does this say about my DNS server? vmnet > this is from vmware. But at the moment i'm not using vmware. I think i have to fill  the DNS servers from my providers and other additional info in the bind configuration. I read something about dns.. let's see if it works.. i will let you know.

---

