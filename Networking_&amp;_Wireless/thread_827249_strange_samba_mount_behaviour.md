---
title: "strange samba mount behaviour"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-06-12
Hi,

I have a win2k server on my network hosting samba shares. I can only access them through IP, yet I can ping the hostname, any idea what might be happening here?

---

### Post by dmizer on 2008-06-13
please post the contents of /etc/nsswitch.conf and /etc/resolv.conf

---

### Post by Geran on 2008-06-13
/etc/resolv.conf ...

search ncci.campus
nameserver 192.168.1.1
nameserver 192.168.100.100


/etc/nsswitch.conf

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by dmizer on 2008-06-15
in order to mount by host name with cifs, you'll have to enable netbios name resolution.

change the "hosts" line in your /etc/nsswitch.conf file so it looks like this:
```
hosts: files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
then install winbind:
```
sudo aptitude install winbind
```

then you should be able to mount by host name.

---

