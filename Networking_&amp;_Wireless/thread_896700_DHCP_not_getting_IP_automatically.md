---
title: "DHCP not getting IP automatically"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Lem0nHead on 2008-08-21
hello
I have 2 computers plugged to a HUB (router behind)
everytime I plug the cable of one of them, it gets its IP and works correctly

but I have a hard time with the other PC, running Ubuntu
I usually have to plug/unplug the cable like 5 to 10 times in order to make it work, but it finally works
it's not a cable problem because, if I boot on windows, it gets the IP with no problems

I don't remember installing any program that manage this "auto get IP when plug cable", so it's probably using Ubuntu's default

any ideas on what I can check/try?

thanks

---

### Post by jerome1232 on 2008-08-21
can you try to see what it gives
```
dhclient eth0
```

---

### Post by Lem0nHead on 2008-08-21
I don't know if it's related, but I found that on /var/log/messages

Aug 21 12:51:52 x dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug 21 12:51:52 x dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug 21 12:51:52 x dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug 21 12:51:52 x dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

and that's the content of /etc/dbus-1/system.d/dhcdbd.conf

```
<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
    <servicedir>/usr/share/dbus-1/services</servicedir>
    <policy user="root">
        <allow own="com.redhat.dhcp"/>
        <allow send_interface="com.redhat.dhcp"/>
        <allow send_destination="com.redhat.dhcp"/>
    </policy>
    <policy context="default">
        <deny own="com.redhat.dhcp"/>
        <deny send_destination="com.redhat.dhcp"/>
        <deny send_interface="com.redhat.dhcp"/>
    </policy>
</busconfig>
```

---

### Post by ne3e on 2008-08-21
Have you tried running updates?
I seem to remember there were some networking issues early on.


John

---

### Post by Lem0nHead on 2008-08-21
I run updated 2 days ago

dhclient works fine

```
# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:b9:66:fd:c9
Sending on   LPF/eth0/00:19:b9:66:fd:c9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.252 -- renewal in 19365 seconds.
```

---

