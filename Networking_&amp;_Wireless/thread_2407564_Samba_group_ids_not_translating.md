---
title: "Samba group ids not translating"
date: 2018-12-05
forum: Networking &amp; Wireless
---

### Post by nickninevah on 2018-12-05
Hi all,
I have a client and server configuration with Samba for the domain controller.  I use Samba to administer several windows machines, but in this case, I'm trying to connect two linux machines, running Ubuntu 18, Samba 4.6.  I have an NFS share setup between my domain controller and client.  I am using Samba for authentication.  The problem is the userid and group id.  It changes when going across the nfs share.  I can't work out why.  Unless I can match up the user and group IDs, my file permissions will never work right.  For example, here are the group ids on the domain side, taken from getent group:

```
DMS\domain admins:x:2512:
DMS\domain users:x:2513:
DMS\domain guests:x:2514:
DMS\domain computers:x:3000020:
DMS\domain controllers:x:3000042:
DMS\schema admins:x:3000007:
DMS\enterprise admins:x:3000006:
DMS\group policy creator owners:x:3000004:
DMS\read-only domain controllers:x:3000043:
DMS\dnsupdateproxy:x:3000044:
DMS\dms_user:x:3104:
DMS\dms user:x:3109:

```

And here are the same groups on the client side:
```
DMS\domain admins:x:50010:
DMS\domain computers:x:50011:
DMS\cert publishers:x:50012:
DMS\domain users:x:50000:
DMS\dnsupdateproxy:x:50013:
DMS\domain guests:x:50014:
DMS\schema admins:x:50015:
DMS\dnsadmins:x:50016:
DMS\dms_user:x:50017:

```


You get the same behavior for the userids.  Nothing matches up.  I tried to follow the samba documentation for IDmaps, but it doesn't see to work for connections between DC and client.

Here is the samba config file for my DC:
```
[global]
    workgroup = dms
    realm = DMS.NET
    netbios name = server
    server string = Zentyal Server
    server role = dc
    server role check:inhibit = yes
    server services = -dns
    server signing = auto
    dsdb:schema update allowed = yes
    ldap server require strong auth = no
    drs:max object sync = 1200


    winbind enum users = yes
    winbind enum groups = yes
    template shell = /bin/bash
    template homedir = /home/%U
    ...
```
     

And here is the samba config on my client side:
```

[global]
   workgroup = DMS
   realm = DMS.NET
   netbios name = client
   security = ADS
   dns forwarder = <redacted>


   # ID map configuration
   idmap config * : backend = tdb
   idmap config * : range = 1000 - 2999
   idmap config * : unix_nss_info = yes


   # ID map configuration for DMS
   idmap config DMS : backend = ad
   idmap config DMS : schema_mode = rfc2307
   idmap config DMS : range = 3000 - 10000
   # idmap_ldb : use rfc2307 = yes


   template homedir = /home/%U
   template shell = /bin/bash
   # winbind refresh tickets = yes
   winbind enum users = yes
   winbind enum groups = yes
   winbind cache time = 60      #higher might make you wait long for updates

```


Any ideas?

---

