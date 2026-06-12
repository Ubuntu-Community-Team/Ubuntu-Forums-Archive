---
title: "NetworkManager - DHCP and Link-Local on the same interface"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by BrianSidebotham on 2016-04-20
Hi everyone,

I'm trying to use nmcli (0.9.10) to try and setup eth0 to have a DHCP and link-local address, but they appear to be mutually exclusive through nmcli.

Through ```
/etc/network/interfaces
``` I used to do:

```

iface eth0 inet dhcp
    
       # Make sure eth0 is always the preferred route
       metric 0
      
       # Add link local route for link-local traffic
       pre-up ip route add 169.254.0.0/16 dev $IFACE
      
       # Add our link local address for technician laptop communication
       pre-up ip addr add 169.254.127.100/16 broadcast 169.254.255.255 dev $IFACE label $IFACE:0
      
       # Do the reverse for rip-down
       pre-down ip addr del 169.254.127.100/16 dev $IFACE label $IFACE:0
       pre-down ip route del 169.254.0.0/16 dev $IFACE

```

Which worked as intended (although with a static IP address for the link-local). Is there anyway of doing this through nmcli, and in particular is there a way of doing this with the link-local ```
ipv4.method
``` property so ```
avahi
``` can be used to grab a good ipv4 link local address?

It's a shame ipv6 link local addresses are not browser-compatible!

---

### Post by BrianSidebotham on 2016-08-15
This is an old thread of mine, but now I have it working and this is a  high Google search ranking I may as well post the solution.

I have the connection marked as `ipv4.method=auto` and I've added a  dispatcher script to /etc/NetworkManager/dispatcher.d/ which this  contents:

```
    #!/bin/sh

    IFACE=$1
    STATUS=$2

    # All wired connections get a link-local address forced on them!
    if [ ! -d "/sys/class/net/${IFACE}/wireless" ]; then
      case ${STATUS} in
        up)
          avahi-autoipd --force-bind -D ${IFACE}
          ;;
        down)
          avahi-autoipd --kill ${IFACE}
          ;;
      esac
    fi
```

---

