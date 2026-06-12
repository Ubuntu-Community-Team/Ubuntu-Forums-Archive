---
title: "Samba not mapping to proper AD Unix attribute UIDs"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by MrMustard on 2013-12-11
Hi all,


So when I authenticate to a samba share as a domain user, it works. Unfortunately the Samba daemon gives me a UID (12500) that's coincidentally the last 5 digits of my SID. This breaks proper ownership mapping because my Unix Attribute AD UID is 45000. The default idmap range in the smb.conf file is 10000-39999. I *assume* this is why it's broken. But when I change it to 10000-99999999 it still doesn't map. 


Can anyone help me pull the correct UID/GUID from AD for remote smb connections?
Thanks!


Here's the pertinent global portion :


passdb backend = tdbsam
allow trusted domains = yes
idmap config * : backend = tdb
idmap config * : range = 10000-99999999
realm = my.domain.com
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind normalize names = yes
template homedir = /mnt
template shell = /bin/sh
aio read size = 4096
aio write size = 4096
idmap backend = ad
idmap gid = 100-99999999
idmap uid = 100-99999999
passdb backend = tdbsam
winbind nss info = rfc2307
winbind separator = +

---

