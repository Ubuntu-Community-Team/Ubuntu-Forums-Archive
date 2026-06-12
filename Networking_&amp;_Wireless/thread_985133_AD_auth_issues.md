---
title: "AD auth issues"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by wtfacoconut on 2008-11-17
Hey I've been rtyinf to get ubuntu to go through AD for auth. I followed the guides but with no success. here's my config scripts and other things: 

Here's my krb5.conf:
-----------------------------------------------------
[logging]
default = FILE10000:/var/log/krb5lib.log

[libdefaults]
ticket_lifetime = 24000
default_realm = NETADMIN.LAB
default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

[realms]
NETADMIN.LAB = {
kdc = NETADMINDCT.NETADMIN.LAB
admin_server = NETADMINDCT.NETADMIN.LAB
default_domain = NETADMIN.LAB
}

[domain_realm]
.domain.internal = NETADMIN.LAB
domain.internal = NETADMIN.LAB
--------------------------------------------------------

My smb.conf:
-------------------------------------------------
[global]
security = ads
netbios name = Ubuntu-11
realm = NETADMIN.LAB
password server = NETADMINDCT.NETADMIN.LAB
workgroup = NETADMIN
idmap uid = 500-10000000
idmap gid = 500-10000000
winbind separator = +
winbind enum users = no
winbind enum groups = no
winbind use default domain = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
domain master = no
------------------------------------------------
and my krb ticket klist thingy:

Valid starting     Expires            Service principal
11/17/08 10:23:20  11/17/08 17:03:20  krbtgt/NETADMIN.LAB@NETADMIN.LAB


Kerberos 4 ticket cache: /tmp/tkt1000
klist: You have no tickets cached
-----------------------------------------------------
thanks in advance

---

### Post by afeishisb75244 on 2008-11-17
[[color=#0000ff]The birth of Ming-Jian[/color]](http://www.runescape-shop.com/em/new-11.php)[[color=#0000ff]Painting ghosts of the most vulnerable[/color]](http://www.runescape-shop.com/em/new-12.php)[[color=#0000ff]In your serious[/color]](http://www.runescape-shop.com/em/new-13.php)[[color=#0000ff]Jian made the people[/color]](http://www.runescape-shop.com/em/new-14.php)[[color=#0000ff]Xian Japan released[/color]](http://www.runescape-shop.com/em/new-15.php)

---

### Post by wtfacoconut on 2008-11-17
??? Uuuuummmmm...sry dude. you lost me...


> **afeishisb75244 said:**
> [[color=#0000ff]The birth of Ming-Jian[/color]](http://www.runescape-shop.com/em/new-11.php)[[color=#0000ff]Painting ghosts of the most vulnerable[/color]](http://www.runescape-shop.com/em/new-12.php)[[color=#0000ff]In your serious[/color]](http://www.runescape-shop.com/em/new-13.php)[[color=#0000ff]Jian made the people[/color]](http://www.runescape-shop.com/em/new-14.php)[[color=#0000ff]Xian Japan released[/color]](http://www.runescape-shop.com/em/new-15.php)

---

