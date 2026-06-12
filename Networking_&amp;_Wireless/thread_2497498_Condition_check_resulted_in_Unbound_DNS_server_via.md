---
title: "Condition check resulted in Unbound DNS server via resolvconf being skipped"
date: 2024-05-08
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2024-05-08
I'm running my own maul server with unbound and have found this message when I start unbound
```
Condition check resulted in Unbound DNS server via resolvconf being skipped
```

The service is up
```
&#9679; unbound.service - Unbound DNS server
     Loaded: loaded (/lib/systemd/system/unbound.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2024-05-08 06:53:15 CEST; 2min 1s ago
       Docs: man:unbound(8)
    Process: 1916129 ExecStartPre=/usr/lib/unbound/package-helper chroot_setup (code=exited, status=0/SUCCESS)
    Process: 1916132 ExecStartPre=/usr/lib/unbound/package-helper root_trust_anchor_update (code=exited, status=0/SUCCESS)
   Main PID: 1916135 (unbound)
      Tasks: 4 (limit: 35955)
     Memory: 18.4M
        CPU: 143ms
     CGroup: /system.slice/unbound.service
             &#9492;&#9472;1916135 /usr/sbin/unbound -d -p

May 08 06:53:15 mail1 systemd[1]: Starting Unbound DNS server...
May 08 06:53:15 mail1 unbound[1916135]: [1916135:0] notice: init module 0: subnet
May 08 06:53:15 mail1 unbound[1916135]: [1916135:0] notice: init module 1: validator
May 08 06:53:15 mail1 unbound[1916135]: [1916135:0] notice: init module 2: iterator
May 08 06:53:15 mail1 unbound[1916135]: [1916135:0] info: start of service (unbound 1.13.1).
May 08 06:53:15 mail1 systemd[1]: Started Unbound DNS server.
May 08 06:53:57 mail1 unbound[1916135]: [1916135:0] info: generate keytag query _ta-4f66. NULL IN

```

There are no errors when I run
```
unbound-checkconf
unbound-checkconf: no errors in /etc/unbound/unbound.conf

```

I have installed resolvconf and /etc/resolvconf/update.d/unbound looks like this

```
#!/bin/sh -e

PATH=/usr/sbin:/usr/bin:/sbin:/bin

if [ ! -x /usr/sbin/unbound ]; then
    exit 0
fi

if [ ! -f /etc/unbound/unbound_control.key ]; then
    exit 0
fi

if [ ! -x /lib/resolvconf/list-records ]; then
    exit 1
fi

RESOLVCONF_FILES="$(/lib/resolvconf/list-records)"

if [ -n "$RESOLVCONF_FILES" ]; then
    NS_IPS="$(sed -rne 's/^[[:space:]]*nameserver[[:space:]]+//p' $RESOLVCONF_FILES \
        | egrep -v '^(127\.|::1)' | sort -u)"
else
    NS_IPS=""
fi

if [ -n "$NS_IPS" ]; then
    FWD="$(echo $NS_IPS | tr '\n' ' ')"
    unbound-control forward $FWD 1>/dev/null 2>&1 || true
else
    unbound-control forward off 1>/dev/null 2>&1 || true
fi

```

Thanks

---

### Post by lister171254 on 2024-05-16
I received the following from the package maintainer

----------------------------------------------------------------------------------------------------------
This is normal and a do-nothing warning.

In debian (and ubuntu), unbound service startup triggers startup of
unbound-resolvconf service too, - this is to tell resolvconf, if it
is present, about unbound presence.

The condition which you're seeing is in unbound-resolvconf.service:

  ConditionFileIsExecutable=/sbin/resolvconf

so the service does nothing if there's no /sbin/resolvconf on your
system.  And systemd is logging this message.  Which is, as I
mentioned earlier, absolutely normal.

Unbound itself works as configured.

This is how the packaging is done in debian.  And while I'm the
maintainer of unbound package in debian, I don't know why it's
done this way, - it was before my time.

Thanks,

/mjt 
----------------------------------------------

---

