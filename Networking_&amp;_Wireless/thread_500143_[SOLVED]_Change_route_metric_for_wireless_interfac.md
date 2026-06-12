---
title: "[SOLVED] Change route metric for wireless interface"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by allan_q on 2007-07-13
In an environment where there are unsecured APs (hotels, neighbors, etc.), iwconfig will automatically associate with those APs even if the laptop is on a wired connection. This results in two default routes--one through wireless and one wired.

Can the metric be changed for the wireless' default route so it is higher than wired connections (e.g. 2000)? This would make traffic go through a wired connection before the wireless. I checked /etc/network/interfaces and the metric is only used for static entries and would not work if the interface is on DHCP. I was also looking at dhclient if an exit-hook script can fix this but I don't know how to write one.

Can someone help? I'm hoping there's a simple fix that I just missed.

---

### Post by allan_q on 2007-07-15
Well, I finally got it to work. Hopefully, this will help some one else. As of this writing, I am running 3.0.4-12ubuntu4 of dhcp3-client under Feisty. I believe future versions changed the script so this may not apply.

[LIST=1]
[*]Edit [FONT="Courier New"]/sbin/dhclient-script[/FONT]. You'll need to move the IF_METRIC block below the run_hookdir as the metric needs to be updates with the enter-hook script later on. Below is a portion of the code.
```
if [ -n "$new_interface_mtu" ] && [ $new_interface_mtu -ge 575 ]; then
    mtu_arg="mtu $new_interface_mtu"
fi
    

# The action starts here

# Invoke the local dhcp client enter hooks, if they exist.
run_hook /etc/dhcp3/dhclient-enter-hooks
run_hookdir /etc/dhcp3/dhclient-enter-hooks.d
    
if [ -n "$IF_METRIC" ]; then
    metric_arg="metric $IF_METRIC"      # interfaces(5), "metric" option
fi  
```

[*]Create a [FONT="Courier New"]wireless[/FONT] file under [FONT="Courier New"]/etc/dhcp3/dhclient-enter-hooks.d/[/FONT] and change the "eth2" to your wireless interface.
```
#!/bin/sh
if [ "$interface" = "eth2" ] && ( [ "$reason" = "BOUND" ] || \
[ "$reason" = "RENEW" ] || [ "$reason" = "REBIND" ] || \
[ "$reason" = "REBOOT" ] ); then
        IF_METRIC="2000"
        logger "Setting interface $interface to $IF_METRIC metric."
fi
```
[*]That's it. [FONT="Courier New"]/var/log/messages[/FONT] will be updated every time this triggers so you'll know when the metric is updated.
[/LIST]

Hope this helps.

---

### Post by Blinkiz on 2008-01-13
Just tried this on Ubuntu 7.10 Gutsy.
It does not work. Tried this on a new installation of ubuntu 7.10.

I can see this line in /va/log/messages
```
Jan 13 07:18:10 blinklap logger: Setting interface wlan0 to 2000 metric.
```
No error code after.

ip route show returns
```
niklas@blinklap:~$ ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.66 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.67 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.254 dev wlan0 
 
```

---

