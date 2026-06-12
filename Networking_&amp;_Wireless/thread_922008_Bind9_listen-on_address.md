---
title: "Bind9 listen-on address"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by taz205 on 2008-09-16
I'm running bind9 on hardy and when I start the process manually, everything works fine. When bind starts as a daemon during boot up, it fails to listen on all the interfaces that it should. It listens on 127.0.0.1 but NOT on 192.168.128.100. If I restart it manually, it binds to 192.168.128.100.

According to syslog, it looks like named might be loading before dhclient (or Network Manager ?) grabs a lease on 128.100. I've tried mv /etc/rc5.d/S15bind9 /etc/rc5.d/s99bind9 but that did do anything. Any thoughts?

---

### Post by glarson on 2008-10-09
So far, the only way I've found to get bind9 to listen on new interfaces that were added after named started is to restart named, i.e.:
   invoke-rc.d bind9 restart

---

### Post by donco on 2010-02-26
Archaic thread, but given that I tend to store much of my memory in google, and this one came up wrong (and I hate that), I thought I'd correct it.

The bind9 option you are looking for is (shown with default value):
/etc/bind/named.conf
```

options {
  interface-interval 0 // no periodic search for new interfaces to bind to
}

```Set to non-zero to have bind/named periodially poll for new interfaces (set in minutes) and start up listeners.  To have bind/named check for new listeners as frequently as possible, set to '1', and bind/named will check minutely.

I have no idea why bind/named won't just listen to 0.0.0.0 (all IPs IP), but it won't and that's the switch to get around it.  :)


Enjoy,
-the donco

---

### Post by YavkatA on 2011-01-14
Bump

---

