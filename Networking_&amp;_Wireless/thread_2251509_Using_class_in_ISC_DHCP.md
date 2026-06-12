---
title: "Using class in ISC DHCP"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by rpugsley on 2014-11-04
Hi there,

I'm configuring a DHCP server but I have some problems.
I have an internal network, where I want allow (192.168.0.0/24) to specified mac address OR host names.
In other hand I have a network for some clients, (192.168.0.1/24) which allows unknown clients.

Can anyone check my config file and tell me what I did wrong?

Thanks.



```

class "autorizados"{ match host-name;}
class "interno"{ match hardware;}

# Allowed external devices
subclass "autorizados" "Mary-PC"; # Mary's notebook
subclass "autorizados" "Francisco-PC"; # Francisco's notebook

# Internal devices
subclass "interno" 0a:1b:a9:e1:3c:20; # computer 1
subclass "interno" 0a:1b:a9:72:3d:ce; # computer 2
subclass "interno" 0a:1b:a9:9b:cb:da; # computer 3
subclass "interno" 00:1b:a9:d0:aa:c1; # DCP-8157DN
subclass "interno" 00:1b:a9:9b:cb:cc; # DCP-8158

ddns-update-style interim;
log-facility local7;


# Network
shared-network Mynetwork {
    authoritative;
    # Clients
    subnet 192.168.1.0 netmask 255.255.255.0 {
        option domain-name-servers 8.8.8.8 , 8.8.4.4;
        authoritative;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.250;
        pool {
            allow unknown-clients;
            range 192.168.1.100 192.168.1.200;
            }
        }
    # Lan 1
    subnet 192.168.0.0 netmask 255.255.255.0 {
        authoritative;
        option domain-name-servers 192.168.0.240 , 8.8.8.8 , 8.8.4.4;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.250;
        # Printers
        group {
            # DCP-8157DN
            host BRN001BA9D0AAB1 {
                hardware ethernet 00:1b:a9:d0:aa:c1;
                fixed-address 192.168.0.24;
                }
            # DCP-8158
            host BRN001BA99BCBDA {
                hardware ethernet 00:1b:a9:9b:cb:cc;
                fixed-address 192.168.0.23;

            }
        # Devices
        group {
            use-host-decl-names on;
            # computer 1
            host computer1 {
                hardware ethernet 0a:1b:a9:e1:3c:20;
                }
            # computer 2
            host computer2{
                hardware ethernet 0a:1b:a9:72:3d:ce;
                }
            # computer 3
            host computer3 {
                hardware ethernet 0a:1b:a9:9b:cb:da;
                }            
            # Mary's notebook
            host Mary-PC {
                }
            # Francisco's notebook
            host Francisco-PC {
                }

        pool {
            deny unknown-clients;
            allow members of "interno";
            range 192.168.0.50 192.168.0.130;
            allow members of "autorizados";
            allow known-clients;
            }
        }
    }



```

---

### Post by rpugsley on 2014-11-05
Sometimes in example, Francisco-pc(an allowed client) is getting dhcp  from clients lan(for unknow users) not from Lan 1(for internal and  allowed users). 
Same happens with clients using mac address in subclass.

---

