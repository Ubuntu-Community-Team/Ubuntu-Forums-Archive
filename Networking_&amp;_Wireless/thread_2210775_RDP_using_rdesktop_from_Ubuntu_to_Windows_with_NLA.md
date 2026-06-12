---
title: "RDP using rdesktop from Ubuntu to Windows with NLA"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by ToniWiki on 2014-03-12
I want to use rdesktop to establish RDP connection with a Windows 2008R2 server. The server started enabling Network Level Authentication (NLA).

By default, the rdesktop which comes with Ubuntu 13.10 (v1.7.1) doesn’t have NLA support. I ended up installing rdesktop 1.8.1 from pmjdebruijn ppa.

My host is not on W2008 server LAN so, according some tutoriales, i need to install and configure the Kerberos client, and then establish a Kerberos ticket for my user with kinit <user>.

That is what i have tried to do:

```
$ sudo apt-get install krb5-user
```

After i answered the package configuration questions my /etc/krb5.conf file appears like:

```
[libdefaults]
        default_realm = SERVER-NAME
...
[realms]
        SERVER-NAME = }
                kdc = XXX.XXX.XXX.XXX
                admin_server = XXX.XXX.XXX.XXX
        }
```

Where SERVER-NAME is the W2008 server name and XXX.XXX.XXX.XXX his public IP. I tried to replace the server name with the server work-group without success (the W2008 is not a domain controller and is not inside other domain).

When i try:

```
$ kinit myuser
```

I get:

```
kinit: Cannot resolve servers for KDC in realm "SERVER-NAME" while getting initial credentials
```

Is there somebody who can help me ?

Thanks.

---

