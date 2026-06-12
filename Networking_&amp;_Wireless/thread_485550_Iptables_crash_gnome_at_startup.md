---
title: "Iptables crash gnome at startup"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by Oleg Petrov on 2007-06-27
Hi All,

Currently I'm working on Ubuntu Edgy.
This may sound really strange, but if iptables are loaded at startup, Gnome does not launch.
I have a script called rc.firewall which activates PPPoE connection and assigns iptables rules.
A typical startup script is placed in /etc/init.d:

```
[root@xxxx]:# more /etc/init.d/firewall 
#!/bin/sh
IPTABLESDIR=/etc/iptables
USAGE="usage: $0 {start|stop}"
case $1 in
    start)
        $IPTABLESDIR/rc.firewall
    ;;
    stop)
        $IPTABLESDIR/rc.nofirewall
    ;;
    *)
        echo $USAGE
        exit 1
    ;;
esac
```

And a link is created for launch at level 2:

```
[root@xxxx]:# ls -la /etc/rc2.d/ | grep fire
lrwxrwxrwx   1 root root   20 2007-06-04 23:35 S99firewall -> /etc/init.d/firewall
```

   Now is the whole story. When Ubuntu loads, it asks me for a login and password (I tried to log both as root and as non-root - no difference) and then ... keeps silence. A monochrome screen with no sign of loading anything else. Then I would reload, boot in 'failsafe terminal' mode, disable this startup script, reload again - everything works. If I launched /etc/rc2.d/S99firewall manually, when the system has already booted, everything would work fine!
   Then I commented out all the lines of 'rc.firewall' and decommented them one by one in order to find out which one makes sense. It turned out to be the first default policy on which the system 'stumbled':

```
$IPTABLES -P INPUT DROP
```

   If needed,  I can provide a complete 'rc.firewall' (with public IPs removed). By now, I'm a bit confused about where to start digging.
Thanks a lot in advance!

---

### Post by kidders on 2007-06-28
Hi there,

I imagine your Gnome is trying to do something network-related that you're deliberately blocking with **iptables -P INPUT DROP**. Your machine won't function unless you allow at least *some* network activity.

---

