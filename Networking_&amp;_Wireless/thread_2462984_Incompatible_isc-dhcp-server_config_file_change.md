---
title: "Incompatible isc-dhcp-server config file change?"
date: 2021-05-31
forum: Networking &amp; Wireless
---

### Post by bls3427 on 2021-05-31
I'm using isc-dhcp-server on Ubuntu and it WAS working fine with the following subnet declaration:


[HTML]subnet 192.168.92.0 netmask 255.255.255.0 {
    option domain-search "foo.com", "dyn.foo.com";
    option broadcast-address 192.168.92.255;
    allow duplicates;
    ddns-updates off;
    pool {
        ddns-updates on;
        allow unknown-clients;
        option domain-name "dyn.foo.com";
        ddns-rev-domainname "dhcp";
        default-lease-time 86400;
        max-lease-time 86400;
        range 192.168.92.101 192.168.92.127;
    }
}
[/HTML]

This was with isc-dhcp-server V4.4.1-2.2-ubuntu6 on it. Today I updated Ubuntu, got isc-dhcp-server V4.4.1-2.2ubuntu6.1 and now isc-dhcp-server complains **"Can't clone pool group"**.


I found that I can put the pool declaration outside of the subnet declaration on the latest isc-dhcp-server on Ubuntu, and it works correctly. Unfortunately, doing this on other Debian distros fails!


Am I totally using subnet and pool incorrectly, or is this an incompatible change in isc-dhcp-server on Ubuntu?


This is important (to me, anyhow), since I have a tool that automatically builds dhcpd.conf from a database, and now it's broken with no easy way to fix other than putting in "do it this way/that way" switches.


Thanks

---

### Post by bls3427 on 2021-06-07
This has been fixed in isc-dhcp-server [COLOR=#333333][FONT=monospace]4.4.1-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]2.2ubuntu6.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]2 [/FONT][/COLOR]

---

