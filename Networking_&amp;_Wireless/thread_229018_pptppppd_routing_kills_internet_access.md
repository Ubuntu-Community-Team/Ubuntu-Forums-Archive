---
title: "pptp/pppd routing kills internet access"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by jakedh on 2006-08-03
I have managed to install and configure pptp. It connects to a machine running samba and a vpn server and everything works for a few seconds then all of my connections die.
I am almost certain that this is a routing issue. In windows there is an option to disable the default gateway. Is there a way to do this in linux?

before connecting
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         my.router       0.0.0.0         UG    0      0        0 eth0

```
after connecting
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```
peer file
```

# tunnel puma, written by pptpconfig $Revision: 1.8 $

# name of tunnel, used to select lines in secrets files
remotename puma

# name of tunnel, used to name /var/run pid file
linkname puma

# name of tunnel, passed to ip-up scripts
ipparam puma

# data stream for pppd to use
pty "pptp ***** --nolaunchpppd "

# domain and username, used to select lines in secrets files
name *****

usepeerdns
require-mppe
refuse-eap
persist

# do not require the server to authenticate to our client
noauth

# end of tunnel file

```

---

