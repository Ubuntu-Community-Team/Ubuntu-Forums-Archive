---
title: "DNS time out, but only on localhost"
date: 2021-08-09
forum: Networking &amp; Wireless
---

### Post by david-novak on 2021-08-09
I configure bind9 and it was working for fine for years. Recently, we changed ISP so I updated the forwarders. I believe all that changed were the forwarders, but now the DNS times out when using nslookup from the server itself.

```
root@server1:/etc/bind# nslookup google.com
;; connection timed out; no servers could be reached

```

It works fine when running the same command from another client on the LAN.

```
$ nslookup google.com
Non-authoritative answer:
Server:  UnKnown
Address:  192.168.0.2


Name:    google.com
Addresses:  2607:f8b0:4009:819::200e
          142.250.191.206

```

What could be blocking access from localhost?

**Update:**

Here is my named.conf.options. Notice that is has allow-query set.

```

// Allow the following to query the DNS.
acl goodclients {
        localhost;      // This host.
        localnets;      // All hosts on the LAN.
        10.8.0.0/24;    // Hosts coming from VPN tunnels.
};


options {
        directory "/var/cache/bind";


        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


        allow-query { goodclients; };


        forwarders {
                // Google DNS servers
                8.8.8.8;
                8.8.4.4;
        };


        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

Also, dns-nameservers is set in /etc/network/interfaces.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0


iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.3
        dns-nameservers 127.0.0.1
        dns-search home.lan
        dns-domain home.lan


#iface eth0 inet dhcp

```

Still, nslookup results in timed out when ran from localhost.

---

