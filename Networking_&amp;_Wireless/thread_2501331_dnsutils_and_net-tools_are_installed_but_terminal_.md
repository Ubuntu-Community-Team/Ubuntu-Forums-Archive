---
title: "dnsutils and net-tools are installed but terminal says command(s) not found"
date: 2024-10-02
forum: Networking &amp; Wireless
---

### Post by paulywalnuts on 2024-10-02
I've installed bind and samba AD-DC, but when I run systemctl status samba-ad-dc, I get the following error:

Failed DNS update with exit code 110 

I've also installed the above listed apps, but when I try to run then for trouble shooting, I'm told they're not found.

I've been searching the 110 error code for a few hours, now, and cannot find a decent solution. Other than to use those tools:(

Here's my smb.conf

# Global parameters
[global]
    dns forwarder = 192.168.1.200
    netbios name = PW
    realm = SOPRANOS.ORG
    server role = active directory domain controller
    workgroup = SOPRANOS
    idmap_ldb:use rfc2307 = yes
    client min protocol = CORE
    client max protocol = SMB3
    client min protocol = NT1

[sysvol]
    path = /var/lib/samba/sysvol
    read only = No

[netlogon]
    path = /var/lib/samba/sysvol/sopranos.org/scripts
    read only = No


TIA, Y'all!


"Of all the things I've lost, I miss my mind the most."

---

