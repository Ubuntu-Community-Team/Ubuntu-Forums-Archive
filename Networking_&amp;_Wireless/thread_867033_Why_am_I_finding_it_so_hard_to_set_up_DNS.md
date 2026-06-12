---
title: "Why am I finding it so hard to set up DNS?"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by davidkahn on 2008-07-22
I have looked over the documentation, and BIND looks well documented, and straight forward.  Yet, simple things don't see to work.  There are two things that I cannotget to work reliably:

[LIST=1]
[*]Get zone data moved from the master DNS server on certiby1 (10.10.10.85) to slave dns server on certiby-dev1 (10.10.10.84)
[*]Have my ISC DHCPd server on certiby1 update zone information on the master DNS server on the same computer.
[/LIST]
Any help would be _really_ appreciated.

David

Here are the DNS config files on on the master server (certiby1, 10.10.10.85):

_named.conf_
```
include "/etc/bind/named.conf.options";

zone "." {
    type hint;
    file "/etc/bind/db.root";
};

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

// Allow DHCP
key certiby1-certiby1. {
    algorithm hmac-md5;
    secret "NOTMYREALSECRETCODE==";
    };

include "/etc/bind/named.conf.local";
```

_named.conf.options_

```
options {
    directory "/var/cache/bind";
    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
    forwarders {
        10.10.10.1;
        };
};    
```

_named.conf.local_

```
zone "10.10.10.in-addr.arpa" {
    type master;
    file "/etc/bind/10.10.10.rev";
    allow-update {
        key certiby1-certiby1.;
        };
    also-notify {
        10.10.10.84;
        };
    notify yes;
        // IP addresses of slave servers allowed to transfer zone.
        allow-transfer {
             10.10.10.84;
             };
    };
zone "lahills.certiby.com" {
    type master;
    file "/etc/bind/lahills.certiby.com.hosts";
    also-notify {
        10.10.10.84;
        };
    notify yes;
        // IP addresses of slave servers allowed to transfer zone.
        allow-transfer {
             10.10.10.84;
             };
    };
zone "viacorita.kahnhome.com" {
    type master;
    file "/etc/bind/viacorita.kahnhome.com.hosts";
    allow-update {
        key certiby1-certiby1.;
        };
    also-notify {
        10.10.10.84;
        };
    notify yes;
        // IP addresses of slave servers allowed to transfer zone.
        allow-transfer {
             10.10.10.84;
             };
    };
```

Here are the DNS config files on on the slave server (certiby-dev1, 10.10.10.84):
[U]
named.conf[/U]
Identical to same file on master server except no key definition for DHCP updates.

_named.conf.options_
Identical to same file on master server.

_named.conf.local_
```
zone "lahills.certiby.com" {
    type slave;
    masters {
        10.10.10.85;
        };
    file "/var/cache/bind/lahills.certiby.com.hosts";
    };
zone "viacorita.kahnhome.com" {
    type slave;
    masters {
        10.10.10.85;
        };
    file "/var/cache/bind/viacorita.kahnhome.com.hosts";
    };
zone "10.10.10.in-addr.arpa" {
    type slave;
    masters {
        10.10.10.85;
        };
    file "/var/cache/bind/10.10.10.rev";
    };
```

Finally, here are the key parts of the DHCPs 

```
# Have DHCP update DNS servers. 
ddns-update-style interim;
key certiby1-certiby1 {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;
    secret NOTMYREALSECRETCODE==;
    }

# Windows PCs Reverse DNS
zone 10.10.10.in-addr.arpa. {
    primary 127.0.0.1;

        # Have DHCP update DNS servers. 
    key certiby1-certiby1;
    }

# Windows PCs
zone viacorita.kahnhome.com. {
    primary 127.0.0.1;

        # Have DHCP update DNS servers.
    key certiby1-certiby1;
    }

# And within the subnet definition
        # Have DHCP update DNS servers. 
        ddns-updates on;
        ddns-domainname "viacorita.kahnhome.com.";
        ddns-rev-domainname "10.10.10.in-addr.arpa.";
        ignore client-updates;
```

---

