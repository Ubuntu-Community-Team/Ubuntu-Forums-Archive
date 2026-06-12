---
title: "How to add WWW entries to my bind zones"
date: 2016-12-16
forum: Networking &amp; Wireless
---

### Post by John_Creane on 2016-12-16
I have a virtual-server configured to serve multiple internal websites (this is just for testing) using Apache & it’s working, however to get to these sites from my local machine I have to edit the host file &add in those virtual hosts 

```

192.168.0.121          www.ipplan.test
192.168.0.121          www.owncloud.test
192.168.0.121          [www.teampass.test]("http://www.teampass.test/")

```

I have configured another Ubuntu VM to act as a DNS server only using bind9 & want to use this to resolve entries for the 3 domains above but I'm unsure how to add entries for websites. I know how to add entries in for hosts such as printers, physical firewalls, desktops but not websites. 


These are my bind configuration files, 

```

 cat named.conf.local 
//
// Do any localconfiguration here
//


// Consider addingthe 1918 zones here, if they are not used in your
// organization
//include"/etc/bind/zones.rfc1918";


zone "test"{ 
  type master;
  file"/etc/bind/db.test";
  };


zone"0.168.192.in-addr.arpa" { 
 type master; 
 notify no; 
 file"/etc/bind/db.reversetest";
 }; 

```

```
john@dns:/etc/bind$cat db.test
;
; BIND data file forlocal loopback interface
;
$TTL    604800
@    IN    SOA    test.                      root.test. (
             20161216        ;Serial
             604800        ;Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )        ;Negative Cache TTL
;
@    IN    NS    ns.test.
ns    IN    A    192.168.0.15


vhost    IN    A    192.168.0.121

```


 ```
cat db.testreverse 
;
; BIND reverse datafile for local loopback interface
;
$TTL    604800
@       IN      SOA    ns.test. root.test. (
                       20161216        ; Serial
                        604800         ; Refresh
                         86400         ; Retry
                       2419200         ; Expire
                        604800 )       ; Negative Cache TTL
;
@       IN      NS     ns.
15      IN      PTR    ns.test.
121     IN      PTR    vhost.test.
```

---

### Post by SeijiSensei on 2016-12-16
First, just to check, if you issue the command "host -t any ns.test" what results do you see? Does it return the value of the A record, 192.168.0.15? (You may need to install the bind9-host package if this doesn't work off the bat.)

If that works, try creating another zone file for owncloud.test with an A record for the name "www" that points to 192.168.0.121.  Restart named, then run "host -t any www.owncloud.test"? Does that return 192.168.0.121?  If so, create two more zone files for the remaining names.

I'm not certain about any of this because I've never configured a name server to act as a top-level domain like your .test.

---

