---
title: "qtap interface for qemu / kvm"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by aBitLater on 2008-02-05
hello,

most of the time I'd like to start my qemu/kvm guest OS (winxp) w/out networking.  the How-to i read said that I could leave out "auto qtap0" from /etc/network/interfaces if I wanted to manually bring it up from the terminal with "sudo ifup qtap0".

I took out the 'auto ifup qtap0', and tried it manually, and it works.  but when i'm done in the guest OS, I do:

```
sudo ifdown qtap0
```

and I get this error:

```
kill: 1: Illegal number: cat /var/run/vde_switch.pid
```

here's the block in the interfaces file, where vde_switch.pid is indicated.

```
# auto qtap0 ### I removed this line ###
iface qtap0 inet static
        address 10.111.111.254
        netmask 255.255.255.0
        pre-up /usr/bin/vde_switch --tap qtap0 --daemon --group vde2-net --mod 775 --mgmtmode 770 --pidfile /var/run/vde_switch.pid
        pre-up /etc/init.d/dnsmasq restart
        up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
        down iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
        post-down kill -s HUP `cat /var/run/vde_switch.pid`
```

anyone know why I see that error?

---

### Post by aBitLater on 2008-02-06
I had to change the following (from /etc/network/interfaces)

```
post-down kill -s HUP `cat /var/run/vde_switch.pid`
```

to:

```
post-down kill -s HUP $(cat /var/run/vde_switch.pid)
```

---

