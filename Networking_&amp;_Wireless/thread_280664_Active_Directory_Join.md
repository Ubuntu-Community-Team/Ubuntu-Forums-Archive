---
title: "Active Directory Join"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by AgentX1 on 2006-10-19
I am having difficulties with my Ubuntu box (dapper) joining the domain and authenticating with active directory. The DC is running Windows 2003 Server SP1. I have tried several methods in joining this box to the domain, first using the SADMS GUI located here: [http://sadms.sourceforge.net/](http://sadms.sourceforge.net/) and the manual way located here: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto). Each method results in the same stoppage point with the following error:

```
[2006/10/19 19:50:51, 0] libads/kerberos.c:ads_kinit_password(164)
  kerberos_kinit_password root@DOMAIN.COM failed: Client not found in Kerberos database
[2006/10/19 19:50:51, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Client not found in Kerberos database
```

This occurs when the computer tries to join the domain. I've searched the Internet for answers......twice...and haven't found anything solid. 

kinit works and pulls a ticket:

```
User@Ubuntu:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: User@DOMAIN.COM

Valid starting     Expires            Service principal
10/19/06 19:57:41  10/20/06 02:37:41  krbtgt/DOMAIN.COM@DOMAIN.COM


Kerberos 4 ticket cache: /tmp/tkt1001
klist: You have no tickets cached
```

I have the following configuration:

```
#[/etc/nsswitch.conf]

passwd: files ldap
group: files ldap
shadow: files ldap
hosts: files dns mdns
networks: files
protocols: db files
services: db files
ethers: db files
rpc: db files
netgroup: nis
--------------------------------------------------------------------------------
#[/etc/krb5.conf]

[libdefaults]
 ticket_lifetime = 24000
 default_realm = DOMAIN.COM
 default_tgs_entypes = rc4-hmac des-cbc-md5
 default_tkt__enctypes = rc4-hmac des-cbc-md5
 permitted_enctypes = rc4-hmac des-cbc-md5
 dns_fallback = yes
[realms]
 DOMAIN.COM = {
 kdc = dcserver
 default_domain = domain.com
 }
[domain_realm]
 .domain.com = DOMAIN.COM
 domain.com = DOMAIN.COM
[appdefaults]
 pam = {
 debug = false
 ticket_lifetime = 36000
 renew_lifetime = 36000
 forwardable = true
 krb4_convert = false
 }
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log
--------------------------------------------------------------------------------
#[/etc/samba/smb.conf]

[global]
 netbios name = Ubuntu
 server string = Samba Server 
 realm = DOMAIN.COM
 workgroup = DOMAIN
 security = ADS
 password server = *
 encrypt passwords = yes
 hosts allow = 192.168.0.0/255.255.255.0 127.
 hosts deny = 0.0.0.0/0.0.0.0
 guest account = nobody
 log file = /var/log/samba/samba.log
 username map = /etc/samba/user.map
 socket options = TCP_noDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
 printcap name = /etc/printcap
 load printers = yes
 dns proxy = no
 obey pam restrictions = yes
 pam password change = yes
 winbind separator = /
 winbind use default domain = yes
 idmap uid = 10000-60000
 idmap gid = 10000-60000
 winbind enum users = yes
 winbind enum groups = yes
 template homedir = /home/%U
 template shell = /bin/bash
 default service = homes
 preload = global homes printers
 valid users = @"DOMAIN/Domain Users"
 admin users = "DOMAIN/Administrator"
[homes]
 comment = Home Directory
 browseable = no
 writable = yes
 valid users = @"DOMAIN/Domain Users"
[users]
 path = /home
 comment = All Home Directories
 browseable = yes
 writable = yes
 valid users = @"DOMAIN/Domain Users"
 admin users = "DOMAIN/Administrator"
 read list = @"DOMAIN/Domain Users"
 write list = @"DOMAIN/Domain Users"
[data]
 path = /data
 comment = Data
 browseable = yes
 writable = yes
 valid users = @"DOMAIN/Domain Users"
 admin users = "DOMAIN/Administrator"
 read list = @"DOMAIN/Domain Users"
 write list = @"DOMAIN/Domain Users"
[printers]
 comment = All Printers
 path = /var/spool/samba
 browseable = no
 guest ok = no
 writable = no
 printable = yes
```

Any ideas? If someone can figure this out, they are the genius of the world.

---

