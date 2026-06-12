---
title: "Likewise-open and nssswitch.conf"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by jefframsey on 2008-06-06
I installed hardy heron, apt-get all updates including kernels, apt-get installed likewise-open, and configured it for my 2003 Active Directory domain. All of this worked great. I can log into my Ubuntu server with my AD accounts. It even automatically creates the user's home dir and everything.

The one thing that I noticed is this: If I do a getent passwd, it does not show my AD accounts. I checked the /etc/nssswitch.conf file, and it is set to use likewise-open.

Shouldn't my getent passwd command show my AD accounts?

Here is my /etc/nssswitch.conf file. I have not edited it by hand at all:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat lwidentity
group:          compat lwidentity
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


#---EOF---

And here is my /etc/samba/lwiauthd:

[global]
    workgroup = TILTON
    security = ads
    passdb backend = tdbsam
    disable netbios = yes
    idmap domains = default
    idmap config default:default = yes
    idmap config default:backend = lwopen
    idmap config default:readonly = yes
    idmap alloc backend = tdb
    idmap alloc config:range = 9000 - 9999
    idmap cache time = 3600
    idmap negative cache time = 300
    winbind cache time = 900
    winbind offline logon = yes
    winbind refresh tickets = yes
    winbind replacement character = ^
    winbind normalize names = yes
    winbind expand groups = 10
    template shell = /bin/bash
    template homedir = /home/%D/%U
    machine password timeout = 2592000
# I added the next two lines manually, pretty standard winbind stuff.
    winbind use default domain = yes
    winbind separator = -
    realm = TMIFP.COM
    use kerberos keytab = yes

#---EOF---

---

### Post by Fatman_UK on 2008-10-14
Have you actually joined the domain? The "domainjoin-cli" command should have returned "SUCCESS" if so.

Two obstacles I had to overcome were mDNS not liking ".local" domains and my DNS not being set up right. In the end I had to:

1. apt-get purge libnss-mdns

and

2. add "192.168.0.1 domain.local" to my hosts file, where 192.168.0.1 is the domain controller [we only have one].

Warning: joining the domain actually crashed my gnome-panel process. Restarting GDM fixed that.

Hope this helps.

---

