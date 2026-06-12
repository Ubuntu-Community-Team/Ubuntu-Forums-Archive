---
title: "tightvnc connection refused when using IP address &amp; accepted with localhost"
date: 2020-01-25
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2020-01-25
ubuntu 1804

using tight vnc NOT tiger vnc
tightvnc connection refused when using IP address & accepted with localhost
Did have gnome desktop installed but switched over to xfce4 xubuntu because I could get tightvnc working but only  for local host. Need it to work for the IP address not the local host.

~/.vnc/xstartup
```

#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec startxfce4

```

start/stop tightvncserver
```

to start server
tightvncserver :1

to stop
tightvncserver -kill :1

```

nmap of vnc ports
```

$ sudo nmap tardis -p 5900,5901,5902
PORT     STATE  SERVICE
5900/tcp closed vnc
5901/tcp open   vnc-1
5902/tcp closed vnc-2

```

---

### Post by The Cog on 2020-01-25
Is it configured to only listen on localhost? Many services come that way so you can test and configure their security locally before reconfiguring them to accept external connections.
This command will show what addresses/ports are listening:
```
sudo ss -lntp
```
It may also be your firewall rules of course.

---

### Post by lance bermudez on 2020-01-25
$ sudo ss -lntp
```

LISTEN   0        5                  0.0.0.0:5901            0.0.0.0:*       users:(("Xtightvnc",pid=31971,fd=3))         
LISTEN   0        128                0.0.0.0:6001            0.0.0.0:*       users:(("Xtightvnc",pid=31971,fd=0)) 

```

and ufw is turned off
```

$ sudo ufw status verbose
Status: inactive

```

---

### Post by The Cog on 2020-01-26
That looks like xtightvnc is listening on all local addresses for ports 5901 and 6001. There should be no difference between connecting on localhost and connecting on other local addresses.
Connections from external sources from elsewhere are another matter, and rely on correct IP routing configuration. 

To verify that you really don't have any firewall rules in operation, run this command - if it returns without printing anything then you really don't have any firewall rules - please check this: ```
sudo iptables-save
```

When you say refused when using IP address, are you trying this from local or from another machine?

---

### Post by lance bermudez on 2020-01-29
$ ssh -L 5901:127.0.0.1:5901 -C -N -l lance 192.168.2.5
then use localhost:5901
gsettings list-recursively org.gnome.Vino

to not have to do the above then set the require-encryption to false
gsettings get org.gnome.Vino require-encryption
gsettings set org.gnome.Vino require-encryption false

---

### Post by The Cog on 2020-01-30
```
ssh -L 5901:127.0.0.1:5901 -C -N -l lance 192.168.2.5
then use localhost:5901
```
I understand that. Looks OK to me. Tunnel 5901 from local PC to the destination's 5901.
Be aware that by default, this tunnel is only listening at your local PC on 127.0.0.1. To get it to listen on all addresses, use:
```
ssh -L 0.0.0.0:5901:127.0.0.1:5901 -C -N -l lance 192.168.2.5 
```

I don't understand what this is all about:
```
gsettings list-recursively org.gnome.Vino

to not have to do the above then set the require-encryption to false
gsettings get org.gnome.Vino require-encryption
gsettings set org.gnome.Vino require-encryption false 
```

---

