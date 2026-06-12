---
title: "DNS &amp; Bind"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by abasel on 2008-09-06
I'm a little lost.

My router is 192.16.1.1
My Linux box which is running Ubuntu 8.04 (server) with safesquid, has a static IP of 192.16.1.2

I'm busy trying to set up DHCP and DNS on the linux box (192.168.1.2)

I keep getting the following when I run sudo /etc/init.d/bind9 restart (I followed [http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/]("http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/")

```
Sep  7 14:39:37 safesquid named[5740]: starting BIND 9.4.2-P1 -u bind
Sep  7 14:39:37 safesquid named[5740]: found 1 CPU, using 1 worker thread
Sep  7 14:39:37 safesquid named[5740]: loading configuration from '/etc/bind/named.conf'
Sep  7 14:39:37 safesquid named[5740]: /etc/bind/named.conf.options:1: unknown option 'search'
Sep  7 14:39:37 safesquid named[5740]: loading configuration: failure
Sep  7 14:39:37 safesquid named[5740]: exiting (due to fatal error)
```

Here are my files:

named.conf.local
```
zone "basemaniahome.com" {
        type master;
        file "etc/bind/zones/baselmaniahome.com.db";
        };

zone "1.168.192.in-addr.arpa" {
        type master;
        file "etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```

baselmaniahome.com.db
```
$TTL 3D
@ IN SOA ns.baselmaniahome.com. admin.baselmaniahome.com. (
   2007062001
   28800
   3600
   604800
   38400
);
baselmaniahome.com.  IN      NS         ns.baselmaniahome.com.
gw             IN      A          192.168.1.1
                       TXT        "Network Gateway"

```

rev.1.168.192.in-addre-arpa
```
@ IN SOA ns1.baselmaniahome.com. admin.baselmaniahome.com. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     ns1.baselmaniahome.com.
1                    IN    PTR    gw.baselmaniahome.com


```

named.conf.options
```
search baselmaniahome.com
nameserver 192.168.1.2
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
                202.89.50.62;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

resolv.conf
```
search baselmaniahome.com
nameserver 202.89.50.62
nameserver 202.89.50.48

```

---

### Post by HalPomeranz on 2008-09-07
The first two lines of your named.conf.options file don't belong:

```

search baselmaniahome.com
nameserver 192.168.1.2

```

Those are configuration statements that would belong in a resolv.conf file.  Not sure how they got into named.conf.

---

### Post by abasel on 2008-09-07
That would have been me trying to "fix" things

Do I delete those lines and then just leave the file as an empty/blank file?

---

### Post by HalPomeranz on 2008-09-08
> **abasel said:**
> Do I delete those lines and then just leave the file as an empty/blank file?

Well, you should delete the two bogus lines, but it looks like you want the other settings that are in that file.

Btw, I see another error, this time in your baselmaniahome.com.db file.  The TXT record line needs to have an "IN" on it, like so:

```

gw             IN      A          192.168.1.1
               IN      TXT        "Network Gateway"

```

---

### Post by technocp on 2009-11-11
Dear Abasel

did you find the way to fix those problems that you have found

because i have been using the same link for setting up local dns and i have been getting the same error as you got

please let me know if you have the solution

Thanks in advance

---

### Post by abasel on 2009-11-11
Shew.. that was a while back... I am sure that I got it working but can't remember how. I have since moved house and dismantled my entire network... planning to rebuild in the next to months ... sorry can't remember

---

### Post by Iowan on 2009-11-11
Depending ho how complicated your network is, **dnsmasq** is pretty simple to set up as DHCP/DNS server.

---

