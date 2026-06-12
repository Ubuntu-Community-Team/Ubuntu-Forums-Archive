---
title: "Home DNS with Bind9 Help"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by kuya1284 on 2007-06-09
Hi Guys,

I've been trying for a while now to get a local DNS Server up and running and I can't seem to figure this out.  I tried performing the steps outlined in [this thread]("http://ubuntuforums.org/showthread.php?t=236093"), but can't seem to perform nslookup from other machines in my LAN.  I also tried searching the web and the forums for a solution, but can't for the life of me get this going.

I'm trying to create a local development environment.  Once a project has been approved and completed, I will upload to a server hosted on the Web.

I have one box running Windows as the host OS.  Ubuntu 7.04 (Desktop) is running as a guest OS in VMWare.  I've got different services running properly, such as Apache2, TeamSpeak, etc. My development files are stored on a DSM-G600 NAS.  Apache sees the files just fine and I can access specific projects through Hostnames defined in both the Linux and Windows Hosts file.

After configuring Bind9, and modifying my resolv.conf file, I am unable to access the projects from within Ubuntu and from any machine in my LAN.  My router is configured such that the first DNS is the IP of Ubuntu (192.168.1.118) and the second is that of the ISP's primary DNS.  I even tested out just manually specifying a DNS in the Windows TCP/IP so that Win can perform it's lookup directly with Ubuntu.  Either way, when I perform an nslookup, it says that the server is unknown and the lookup fails. When I start Bind9, I get the OK everytime, but still no joy with performing lookups.

1. Do I need to setup my environment to be running as a Domain?

2. Could anyone please tell me if I need to make any changes to the following?

**Router's Internal IP:** 192.168.1.100
**Ubuntu's IP:** 192.168.1.118

**named.conf.local**
```
zone "railnrebels.lan" {
type master;
file "/etc/bind/zones/railnrebels.lan.zone";
};

zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```

**named.conf.options**
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

        // forwarders {
        //      0.0.0.0;
        // };
        forwarders {
                192.168.1.100;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };

        // By default, name servers should only perform recursive domain
        // lookups for their direct clients.  If recursion is left open
        // to the entire Internet, your name server could be used to
        // perform distributed denial of service attacks against other
        // innocent computers.  For more information on DDoS recursion:
        // http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987

        allow-recursion { localnets; };

        // If you have DNS clients on other subnets outside of your
        // server's "localnets", you can explicitly add their networks
        // without opening up your server to the Internet at large:
        // allow-recursion { localnets; 192.168.0.0/24; };

        // If your name server is only listening on 127.0.0.1, consider:
        // allow-recursion { 127.0.0.1; };
};
```

**railnrebels.lan.zone**
```
railnrebels.lan.        IN      SOA     ns1.railnrebels.lan. admin.railnrebels.lan. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name
railnrebels.lan.        IN      NS      ns1.railnrebels.lan.
//example.com. IN MX 10 mail.example.com.


// Replace the IP address with the right IP addresses.
www   IN      A       192.168.1.118
//mta   IN      A       192.168.1.118
ns1     IN      A       192.168.1.118

```


**rev.1.168.192.in-addr.arpa**
```
@       IN      SOA     ns1.railnrebels.lan.    admin.railnrebels.lan. (
2007031001;
28800;
604800;
604800;
86400
)

        IN      NS      ns1.railnrebels.lan.
118     IN      PTR     railnrebels.lan

```

**resolv.conf**
```
search railnrebels.lan
nameserver 192.168.1.118
nameserver 192.168.1.100

```

When I perform **dig railnrebels.lan**, I get

```
; <<>> DiG 9.3.4 <<>> railnrebels.lan
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 49620
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;railnrebels.lan.               IN      A

;; Query time: 3 msec
;; SERVER: 192.168.1.118#53(192.168.1.118)
;; WHEN: Sat Jun  9 12:51:48 2007
;; MSG SIZE  rcvd: 33
```

Could some please help.  Thank you in advance.

---

### Post by kuya1284 on 2007-06-09
Nevermind, I think I figured things out.  When using named-checkzone, I discovers a bunch of syntax errors which were being caused by the "//" comments.  I guess we're supposed to be using ";" for comments in the zone files.  The person who created the [writeup]("http://ubuntuforums.org/showthread.php?t=236093") should probably consider rewriting his information using the correct syntax for comments, so as not to confuse noobs like me.  I also he used hases (#) in the config file when he should be using "//".

Anyway, I got things working and I'm a lot happier now. :popcorn:

I guess the only issue that I have left to figure out is to determine why my router won't point to the DNS server.  I specified the IP address of the server in the router's configuration; however, when I attempt to access a webpage on the server, it will not resolve.  I had to manually configure the Windows TCP/IP DNS settings to point to the DNS server. Hmmm... oh well, I guess I'll figure that out later since that's a whole separate issue.  if anyone has had any luck in this, I would appreciate some help.  My router is a Dlink DGL-4300.

Cheers

---

