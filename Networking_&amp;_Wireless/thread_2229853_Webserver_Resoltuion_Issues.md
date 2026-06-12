---
title: "Webserver Resoltuion Issues"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by TheHackMan on 2014-06-15
A couple months ago I made some adjustments to my webserver to get it back online and for about three weeks afterwards I could get to my internal websites without issue. One day however it would no longer resolve the domain name properly and the only way to get to it is to use the local IP address however I want to be able to access it using the internal website address again. I'm not sure why it would suddenly stop working properly after a period of time. I made no system changes after I got it up and working so I'm pretty stumped as to whats going on.

I've also noticed another issue with SSH into the server itself. For a long time when I would open up an SSH session and it would ask for the username and right after the password. Now Ill open up an SSH session, input the username, and it hangs for 20 or so seconds before prompting for the password. After entering the password it seems to hang again for a few seconds before giving more output.


I'm not exactly sure which files to begin looking in for possible causes of the problem and the webserver issues are what concern me the most since the SSH delay seemed to happen no long after the websites stopped resolving correctly.


I am using Ubuntu 14.04 LTS however the issues began back in 12.04 LTS

---

### Post by SeijiSensei on 2014-06-15
Your domain name resolution is broken.  How do you resolve internal names?  Are you running an internal DNS server or using /etc/hosts entries?

---

### Post by TheHackMan on 2014-06-16
I'm using entries on /etc/hosts along with bind9

My IPv4 portion of /etc/hosts is as follows:
127.0.0.1       localhost.localdomain   localhost
192.168.1.77    orion.int       orion

I only have the single domain right now. I had planned to add more but since things aren't working properly for some reason I'm holding off on trying to add more to make fixing it less painful


My bind files are as follows:

/etc/bind/named.conf.local
> zone "orion.int" {
        type master;
        file "/etc/bind/db.orion.int";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
//      file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";

};


/etc/bind/db.orion.int
> 
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.orion.int. root.orion.int. (
                             15         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.orion.int.
@       IN      A       192.168.1.77
@       IN      AAAA    ::1
ns      IN      A       192.168.1.77
orion.int.      IN      A       192.168.1.77
[www.orion.int](www.orion.int).  IN      A       192.168.1.77
; www   IN      A       192.168.1.77
@       IN      MX      orion.int.
@       IN      TXT     "v=spfl a mx ~all"




/etc/bind/db.192
> ; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.orion.int. root.orion.int. (
                             17         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;

;       IN      NS      orion.int.

@       IN      NS      ns.
1.0.0   IN      PTR     localhost.
1       IN      PTR     router.int.
10      IN      PTR     ns.orion.int.
77      IN      PTR     orion.int.



/etc/bind/db.local
> ; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     localhost. root.localhost. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1


---

