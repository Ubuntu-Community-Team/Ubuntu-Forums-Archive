---
title: "Samba - Become Domain Member Windows 2003"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by orudie on 2008-10-04
Greetings!

After a few days of trying this decided to start a new thread on this problem. Followed instructions on this thread, its pretty old but I guess it would still apply today. 

[http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)


Domain Name: orudie.command.center
The old type domai: ORUDIE
Full computer name orudie-d6e76825.orudie.command.center


Let me show you my config files. 

[COLOR="Blue"]/etc/krb5.conf[/COLOR]

```
[logging]
    default = FILE10000:/var/log/krb5lib.log
[libdefaults]
    ticket_lifetime = 24000
    default_realm = COMMAND.CENTER
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
[realms]
    COMMAND.CENTER = {
        kdc = orudie.command.center
        admin_server = orudie.command.center
        default_domain = COMMAND.CENTER
}
[domain_realm]
    .command.center = COMMAND.CENTER
    command.center = COMMAND.CENTER


```
[COLOR="Blue"]/etc/hosts[/COLOR]
```
127.0.0.1       localhost
#127.0.1.1      ubuntu

127.0.1.1   orudie.command.center localhost orudie-d6e76825
24.189.232.10 orudie-d6e76825

```
[COLOR="Blue"]/etc/samba/smb.conf[/COLOR]

```
[global]
        security = ads
        netbios name = orudie-D6E76825
        realm = COMMAND.CENTER
        password server = ORUDIE.COMMAND.CENTER
        workgroup = ORUDIE
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
[data]
comment = Backup Server
path = /media/500gbBackup
read only = Yes
guest only = Yes
```

[COLOR="Blue"]testparm[/COLOR] 

```
orudie@ubuntu:/home$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[data]"
Loaded services file OK.
'winbind separator = +' might cause problems with group membership.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
        workgroup = ORUDIE
        realm = COMMAND.CENTER
        netbios name = ORUDIE-D6E76825
        security = ADS
        password server = ORUDIE.COMMAND.CENTER
        domain master = No
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        template shell = /bin/bash
        winbind separator = +
        winbind use default domain = Yes

[data]
        comment = Backup Server
        path = /media/500gbBackup
        guest only = Yes

```
[COLOR="Blue"]/etc/default/ntpdate[/COLOR]
```
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=yes

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="ntp.ubuntu.com" "orudie.command.center"

# Additional options to pass to ntpdate
NTPOPTIONS="-u"

```

[COLOR="Blue"]/etc/nsswitch.conf[/COLOR]

```
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns wins
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

```
So far I am only able to 'ping orudie.command.center'

[COLOR="Red"]ERROR[/COLOR]

orudie@ubuntu:/home$ kinit [email]Administrator@COMMAND.CENT[/email]ER
kinit(v5): Cannot contact any KDC for realm 'COMMAND.CENTER' while getting initial credentials

I also tried without lower case same error. And when trying to run orudie@ubuntu:/home$ kinit [email]Administrator@ORUDIE.COMMAND.CENT[/email]ER
kinit(v5): Cannot resolve network address for KDC in realm ORUDIE.COMMAND.CENTER while getting initial credentials

---

