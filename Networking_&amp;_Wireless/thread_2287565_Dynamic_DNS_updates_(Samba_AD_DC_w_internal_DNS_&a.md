---
title: "Dynamic DNS updates (Samba AD DC w/ internal DNS &amp; isc-dchp-server)"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by nprecup on 2015-07-20
I've been searching the internet for any clues as to how to make dynamic DNS updates work with my current configuration, but to no avail.

My system:
Ubuntu 14.04 server
Samba AD DC version 4.2.3 (with Internal DNS)
isc-dhcp-server version 4.2.4

Almost everything works as expected. DHCP works, I can add and remove computers and users from the domain, etc. The problem is that DNS updates seem to be only occurring while joining computers to the domain, and at no other time.

In the syslog, I often get this event:
> Jul 20 11:11:53 ubuntuDC dhcpd: Unable to add forward map from laptop.EXAMPLE.local to 10.19.39.101: not found

dhcpd.conf has
> ddns-updates on;
ddns-update-style interim;
update-static-leases on;


allow-unknown-clients;
one-lease-per-client true;
deny duplicates;
ignore client-updates;



option domain-name "EXAMPLE.local";
option domain-name-servers 10.19.39.2;


default-lease-time 600;
max-lease-time 7200;


authoritative;


log-facility local7;


subnet 10.19.39.0 netmask 255.255.255.0 {
  range 10.19.39.101 10.19.39.140;
}




smb.conf has:
> [global]
        workgroup = EXAMPLE
        realm = EXAMPLE.local
        netbios name = UBUNTUDC
        server role = active directory domain controller
        dns forwarder = 10.19.39.2
        allow dns updates = signed
        log level = 3
        log file = /var/log/syslog
        debug timestamp = Yes


[netlogon]
        path = /usr/local/samba/var/locks/sysvol/kwt.lab/scripts
        read only = Yes


[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = Yes




We have a small network (~30 machines), and often have a need to temporarily add client machines to the network without fully joining them to the domain. We need dynamic updates to work, but I don't know what to try now.

Since everything else is working very well, it would be nice to be able to use the internal DNS backend, but if I have to I could switch to BIND9. I tried that one afternoon. It wasn't pretty, but with time I could figure it out.

Any input on how to solve this problem is much appreciated.

---

