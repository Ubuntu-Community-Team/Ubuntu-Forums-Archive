---
title: "nslookup uses server 127.0.0.53"
date: 2019-02-02
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2019-02-02
I'm on the latest LTS server version of Ubuntu with unbound dns server and netplan config

My netplan yaml looks like this

```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: yes
      nameservers:
              search: [contaboserver.net]
              addresses: [127.0.0.1]

```

a nslookup shows

```
nslookup denic.de
Server:		127.0.0.53
Address:	127.0.0.53#53

```

Why is this not going to 127.0.0.1

Thanks

---

### Post by lister171254 on 2019-02-02
Ok. I think I found the culprit

```
sudo more /etc/resolv.conf 
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
search contaboserver.net

```

Not sure why this file is there. I thought netplan is meant to replace all this

---

