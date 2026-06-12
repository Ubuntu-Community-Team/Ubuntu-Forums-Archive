---
title: "Installing Arch in VBox - networking..."
date: 2009-03-23
forum: New to Ubuntu
---

### Post by earthpigg on 2009-03-23
using the arch [beginner's guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"), i have gotten to the networking portion. my router is set up for dhcp.

```
ping -c 3 www.google.com
```

returns

```
--- www.1.google.com ping statistics ---
3 packets transmitted, 0 recieved, 100% packet loss, time 2015
```

relevant contents of /etc/rc.conf:

```
HOSTNAME="myhost"
```

also tried duplicating my computer's host name.

```
eth0="dhcp"
INTERFACES=(eth0)
```

also tried running 

```
dhcpcd eth0
```

from the terminal after killing the other process.

---

### Post by Xiong Chiamiov on 2009-03-23
Asking at the Arch forums is going to get you much better help, since most people here have no idea how rc.conf works.  See you there.

---

