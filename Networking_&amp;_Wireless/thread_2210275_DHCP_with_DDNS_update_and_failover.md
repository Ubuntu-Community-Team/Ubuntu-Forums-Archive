---
title: "DHCP with DDNS update and failover"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by dispair1981 on 2014-03-10
Hello,

     I had posted once before here about a problem with [DDNS updates to bind9 from isc-dhcp-server]("http://ubuntuforums.org/showthread.php?t=2209487").  Since that post I do have the DDNS working on one server, however now I am trying setup failover so I can have one server down for edits, or if any problems arise.  The two servers communicate well:
```

Mar 10 00:36:00 Kerberus dhcpd: failover peer dhcp-failover: I move from communications-interrupted to startup
Mar 10 00:36:15 Kerberus dhcpd: failover peer dhcp-failover: I move from startup to communications-interrupted
Mar 10 00:38:19 Kerberus dhcpd: failover peer dhcp-failover: peer moves from normal to normal
Mar 10 00:38:20 Kerberus dhcpd: failover peer dhcp-failover: I move from communications-interrupted to normal

```

However, I am unable to get the secondary server to write the DDNS records.

```

Mar 10 00:38:29 Kerberus named[2865]: client 192.168.1.15#60672/key rndc-key: signer "rndc-key" denied
Mar 10 00:38:29 Kerberus named[2865]: client 192.168.1.15#60672/key rndc-key: update forwarding 'home.com/IN' denied
Mar 10 00:38:30 Kerberus dhcpd: DHCPREQUEST for 192.168.1.22 from 34:23:ba:11:26:b8 (android-f3838621a6e7b6bc) via p2p1
Mar 10 00:38:30 Kerberus dhcpd: DHCPACK on 192.168.1.22 to 34:23:ba:11:26:b8 (android-f3838621a6e7b6bc) via p2p1
Mar 10 00:38:30 Kerberus dhcpd: Unable to add forward map from android-f3838621a6e7b6bc.home.com to 192.168.1.22: REFUSED

```

I can see from the above that bind9 is refusing the key rndc-key for home.com, however, in my named.config.local I have the key setup properly for both zones.

/etc/bind/named.conf.local

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

key "rndc-key" {
        algorithm hmac-md5;
        secret "6uxIH8jAn8dwKa99mvM1oA==";
};

controls {
        inet 127.0.0.1 allow {
                localhost;
                192.168.1.10;
                192.168.1.15;
        }
        keys {
                "rndc-key";
        };
};

zone "home.com" {
        type slave;
        file "/var/cache/bind/db.home.com";
        allow-update { key "rndc-key"; };
        #allow-transfer {192.168.1.0/24; };
        notify yes;
        masters {192.168.1.10;};
};

zone "1.168.192.in-addr.arpa" {
        type slave;
        file "/var/cache/bind/db.192.home.com";
        allow-update { key "rndc-key"; };
        #allow-transfer {192.168.1.0/24; };
        notify yes;
        masters {192.168.1.10;};
};

```

This is the exact same named.conf.local as the primary where the DDNS updates are working.

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

key "rndc-key" {
        algorithm hmac-md5;
        secret "6uxIH8jAn8dwKa99mvM1oA==";
};

controls {
        inet 127.0.0.1 allow {
                localhost;
                192.168.1.10;
                192.168.1.15;
        }
        keys {
                "rndc-key";
        };
};

zone "home.com" {
        type master;
        file "/var/cache/bind/db.home.com";
        allow-update { key "rndc-key"; };
        allow-transfer {192.168.1.0/24;};
        notify yes;
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/var/cache/bind/db.192.home.com";
        allow-update { key "rndc-key"; };
        allow-transfer {192.168.1.0/24;};
        notify yes;
};

```

and the dhcpd.conf is also setup with the exact same key on both the secondary

```

#
# /etc/dhcpd.conf for secondary DHCP server
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)

#ddns-updates on;
ddns-update-style interim;
update-static-leases on;

key "rndc-key" {
        algorithm hmac-md5;
        secret "6uxIH8jAn8dwKa99mvM1oA==";
};

allow unknown-clients;
use-host-decl-names on;

# option definitions common to all supported networks...
option domain-name "home.com";
option domain-name-servers 192.168.1.10, 192.168.1.15, 192.168.1.1;
default-lease-time 800;
max-lease-time 1600;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#Building DNS Zones
zone    home.com. {
        primary 192.168.1.15;
        key rndc-key;
}
zone 1.168.192.in-addr.arpa. {
        primary 192.168.1.15;
        key rndc-key;
}

# DHCP Failover configuration

failover peer "dhcp-failover" {
  secondary; # declare this to be the secondary server
  address 192.168.1.15;
  port 647;
  peer address 192.168.1.10;
  peer port 647;
  max-response-delay 30;
  max-unacked-updates 10;
}

subnet 192.168.1.0 netmask 255.255.255.0 {
        option subnet-mask 255.255.255.0;
        option domain-name-servers 192.168.1.10, 192.168.1.15;
        option domain-name "home.com";
        option routers 192.168.1.1;

        # Set the address pool for the secondary server.
        pool {
                failover peer "dhcp-failover";
                max-lease-time 900; # 15 minutes
                range 192.168.1.20 192.168.1.60;
                allow unknown-clients;
        }

        default-lease-time 900; # 15 minutes
        max-lease-time 1800;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

```

and the primary server.

```

#
# /etc/dhcpd.conf for primary DHCP server
#



# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)

#ddns-updates on;
ddns-update-style interim;
update-static-leases on;

key "rndc-key" {
        algorithm hmac-md5;
        secret "6uxIH8jAn8dwKa99mvM1oA==";
};

allow unknown-clients;
use-host-decl-names on;

# option definitions common to all supported networks...
option domain-name "home.com";
option domain-name-servers 192.168.1.10, 192.168.1.15, 192.168.1.1;
default-lease-time 800;
max-lease-time 1600;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

#Building DNS Zones
zone    home.com. {
        primary 192.168.1.10;
        key rndc-key;
}
zone 1.168.192.in-addr.arpa. {
        primary 192.168.1.10;
        key rndc-key;
}

# DHCP Failover configuration

failover peer "dhcp-failover" {
        primary; # declare this to be the primary server
        address 192.168.1.10;
        port 647;
        peer address 192.168.1.15;
        peer port 647;
        max-response-delay 30;
        max-unacked-updates 10;
        load balance max seconds 3;
        mclt 1800;
        split 128;
}

subnet 192.168.1.0 netmask 255.255.255.0 {
#       range 192.168.1.20 192.168.1.60;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 192.168.1.10, 192.168.1.15;
        option domain-name "home.com";
        option routers 192.168.1.1;

        # Set the address pool for the secondary server.
        pool {
                failover peer "dhcp-failover";
                range 192.168.1.20 192.168.1.60;
                max-lease-time 900; # 15 minutes
                allow unknown-clients;
        }

        default-lease-time 900; # 15 minutes
        max-lease-time 1800;

#       ddns-updates on;
#       ddns-domainname "home.com.";
#       ddns-rev-domainname "in-addr.arpa.";
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

```

I have also checked file permissions for the folder and files, the folder is

```

drwxrwxr-x  2 bind bind 4096 Mar 10 01:27 bind

```

and the files are: 

```

randy@Kerberus:/var/cache/bind$ ls -l
total 20
lrwxrwxrwx 1 root root   14 Mar  9 18:12 db.0 -> /etc/bind/db.0
lrwxrwxrwx 1 root root   16 Mar  9 18:12 db.127 -> /etc/bind/db.127
-rwxrwxr-x 1 root root  473 Mar 10 01:34 db.192.home.com
lrwxrwxrwx 1 root root   16 Mar  9 18:12 db.255 -> /etc/bind/db.255
lrwxrwxrwx 1 root root   18 Mar  9 18:12 db.empty -> /etc/bind/db.empty
-rwxrwxr-x 1 bind bind 1158 Mar 10 01:27 db.home.com
-rw-r--r-- 1 bind bind 5217 Mar 10 01:13 db.home.com.jnl
lrwxrwxrwx 1 root root   18 Mar  9 18:12 db.local -> /etc/bind/db.local
lrwxrwxrwx 1 root root   17 Mar  9 18:12 db.root -> /etc/bind/db.root
-rw-r--r-- 1 bind bind  221 Mar  9 21:46 managed-keys.bind

```

Originally all the files were links, however it would appear that bind9 has replaced these with its own copies of the files.
I have also noticed that the files db.192.home.com and db.home.com become corupted intermittently.

Any ideas?

---

### Post by dispair1981 on 2014-03-10
I don't know if anyone is looking into this for me but i found the problem.  The slave servers can not update their own records.  They have to update the primary.  While i find this a little bit of a hassle because if the primary goes down none of the records get updated.  However the slave can update the primary and then the records trickle down so, it works ehhhh.

The reason for the original problem was found here: [http://www.zytrax.com/books/dns/ch7/xfer.html#update-policy](http://www.zytrax.com/books/dns/ch7/xfer.html#update-policy)

"This statement is mutually exclusive with update-policy and applies to master zones only."

```
allow-update { key "rndc-key"; };
```

there for i had to change the zones to:

```

zone "home.com" {
        type slave;
        file "/var/cache/bind/db.home.com";
        allow-update-forwarding {127.0.0.1; 192.168.1.15; };
        allow-notify {192.168.1.10; };
        allow-transfer {192.168.1.10; };
        masters {192.168.1.10;};
};

zone "1.168.192.in-addr.arpa" {
        type slave;
        file "/var/cache/bind/db.192.home.com";
        allow-update-forwarding {127.0.0.1; 192.168.1.15; };
        allow-notify {192.168.1.10; };
        allow-transfer {192.168.1.10; };
        masters {192.168.1.10;};
};

```

---

