---
title: "samba authentication failures since samba4 upgrade"
date: 2016-12-15
forum: Networking &amp; Wireless
---

### Post by fomember on 2016-12-15
We are running an environment with > 100 Ubuntu hosts (Servers and Workstations 14.04LTS and 16.04LTS)
Our machines are joined to a windows AD user accounts are in a domain which is centrally managed by the company.
We do not have any admin rights on the account domain.
For our clients we have a resource domain which has a one way trust to the account domain.
We also need to use a users.map because our local linux users are not allowed to be added to the account domain.
Since samba4 with winbind and kerberos we frequently loose samba connectivity.
We see error messages in /var/log/samba/log.wb-AccountDomain which say:
  gss_init_sec_context failed with [ Miscellaneous failure (see text): Server (cifs/USxyz@resourceDomain.a.b.c) unknown]
  gss_init_sec_context failed with [ Miscellaneous failure (see text): Server **(krbtgt/Accountdomain.d.e.f@resourceDomain.a.b.c)** unknown]

Especially the krbtgt errors look very strange to me.
Is there possibly some configuration we are missing?

This is the global section of our smb.conf
[global]
  debug level = 0
  syslog      = 0
  oplocks        = False
  level2 oplocks = False
  kernel oplocks = false
   workgroup = RSRCDOM
   realm     = rsrcdom.bbl.ms.philips.com
   security = DOMAIN
   password server = *
   encrypt passwords = yes
   browse list = no
   browseable  = no
  local master = no
  log file = /var/log/samba/log.%m
   max log size = 50
   lock directory = /var/lock/samba/locks
   guest account = smbguest
   map to guest  = Never
   username map = /etc/samba/users.map
   create mask = 0644
   force directory mode = 0775
   directory mask = 0775
   dead time = 240
   dos filetime resolution = true
   server string = Linux Samba %v
   printing      = bsd
   printcap name = /dev/null
   unix extensions = no
   acl allow execute always  = True
  include = /etc/samba/shares.conf

---

