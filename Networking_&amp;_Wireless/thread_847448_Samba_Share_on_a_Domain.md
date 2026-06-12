---
title: "Samba Share on a Domain"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by proxied on 2008-07-02
I'm having a problem setting up a share in samba properly. I'm trying to set it up to where I have domain level security on my single share. I've joined the domain successfully and I'm having no problem using wbinfo to retrieve domain members and groups.

The share itself should be prompting me for a username and password when I try to access it from a machine not on the domain, but it doesn't. It never prompts for a user/pass regardless of whether I use a machine on the domain or not.

Here's a dump of testparm and the output it gives of my smb.conf:
```
$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[k$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
    workgroup = RHCC
    realm = DOMAIN.ORG
    server string = %h server (Samba, Ubuntu)
    security = ADS
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins server = 192.168.0.11
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap uid = 10000-20000
    invalid users = root

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[k$]
    path = /mnt/kdrive
    force user = john
    read only = No
    create mask = 0775
    directory mask = 0775
    guest ok = Yes
```and here's my kerberos config, krb5.conf:
```
[libdefaults]
    default_realm = domain.org
    krb4_config = /etc/krb.conf
    krb4_realms = /etc/krb.realms
    kdc_timesync = 1
    ccache_type = 4
    forwardable = true
    proxiable = true
    v4_instance_resolve = false
    v4_name_convert = {
        host = {
            rcmd = host
            ftp = ftp
        }
        plain = {
            something = something-else
        }
    }
    fcc-mit-ticketflags = true

[realms]
    RHCHURCH.ORG = {
        kdc = rhccbdc.domain.org
        admin_server = rhccbdc.domain.org
    }

[domain_realm]
    .domain.org = rhccbdc.domain.org
    domain.org = rhccbdc.domain.org

[login]
    krb4_convert = true
    krb4_get_tickets = false
```Any ideas?

---

