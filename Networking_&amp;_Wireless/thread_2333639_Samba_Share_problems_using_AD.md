---
title: "Samba Share problems using AD"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by jcarvalho on 2016-08-11
I have an AD domain in Windows Server Enterprise 2008 R2. The domain name is ferreiradias.local I have installed a xubuntu box 16.04 with all updates done. I have installed samba, winbind and krb5-client and ntp and configured them.

krb5.conf:

[libdefaults]
ticket_lifetime = 24h
default_realm = FERREIRADIAS.LOCAL
forwardable = true
dns_lookup_realm = true
dns_lookup_kdc = true
[realms]
FERREIRADIAS.LOCAL = {
kdc = 192.168.1.3:88
admin_server = DC-FD.FERREIRADIAS.LOCAL
default_domain = FERREIRADIAS.LOCAL
}
[domain_realm]
.FERREIRADIAS.LOCAL = FERREIRADIAS.LOCAL
FERREIRADIAS.LOCAL = FERREIRADIAS.LOCAL
.ferreiradias.local = FERREIRADIAS.LOCAL
ferreiradias.local = FERREIRADIAS.LOCAL
[kdc]
profile = /etc/krb5kdc/kdc.conf
[appdefaults]
pam = {
debug = false
ticket_lifetime = 36000
renew_lifetime = 36000
forwardable = true
krb4_convert = false
}
[logging]
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmin.log
default = FILE:/var/log/krb5lib.log

 

nssswitch.conf

passwd:         files winbind
group:          files winbind
shadow:         files winbind

hostname

nas1

hosts

127.0.0.1   localhost
127.0.1.1   nas1.ferreiradias.local nas1.ferreiradias nas1

I could add the linux box to the AD. Everything ok until that point.

smb.conf

 

[global]
security = ADS
realm = FERREIRADIAS.LOCAL
password server = 192.168.1.3
workgroup = ferreiradias
idmap config * : range = 10000-20000
server string = Linuxserver
winbind enum users = yes
winbind enum groups = yes
winbind cache time = 10
winbind use default domain = yes
winbind nested groups = yes
template homedir = /home/%U
template shell = /bin/bash
client use spnego = yes
ntlm auth = yes
lanman auth = no
client ntlmv2 auth = yes
encrypt passwords = yes
restrict anonymous = 2
domain master = no
local master = no
preferred master = no
os level = 0
map to guest = bad user
guest account = nobody
unix extensions = yes

[partilha1]
comment = Marketing
path = /sharing/
valid users =@FERREIRADIAS\jorgcar
writable = yes
read only = no
force create mode = 0777
create mask = 0777
directory mask = 0777
force directory mode = 0777
access based share enum = yes
hide unreadable = yes

 

The problem is when I try to access the linux box via Windows 10 / 7, I have "access denied" error. Can someone point me some guides? Really stuck on this

 

thank you!

---

