---
title: "DHCP not working"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-01-15
I am trying to hand out IP addresses on my internal lan.  Here is the status:

```
systemctl status dnsmasq.service&#9679; dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server
   Loaded: loaded (/lib/systemd/system/dnsmasq.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/dnsmasq.service.d
           &#9492;&#9472;50-dnsmasq-$named.conf, 50-insserv.conf-$named.conf
   Active: active (running) since Mon 2018-01-15 13:42:01 EST; 10min ago
 Main PID: 2974 (dnsmasq)
   CGroup: /system.slice/dnsmasq.service
           &#9492;&#9472;2974 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -r /var/run/dn


Jan 15 13:42:00 server dnsmasq[2960]: dnsmasq: syntax check OK.
Jan 15 13:42:00 server dnsmasq[2974]: started, version 2.75 cachesize 150
Jan 15 13:42:00 server dnsmasq[2974]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHC
Jan 15 13:42:00 server dnsmasq-dhcp[2974]: DHCP, IP range 192.168.1.5 -- 192.168.1.253, lease
Jan 15 13:42:00 server dnsmasq[2974]: no servers found in /var/run/dnsmasq/resolv.conf, will
Jan 15 13:42:00 server dnsmasq[2974]: read /etc/hosts - 5 addresses
Jan 15 13:42:01 server dnsmasq[2974]: reading /var/run/dnsmasq/resolv.conf
Jan 15 13:42:01 server dnsmasq[2974]: using nameserver 8.8.8.8#53
Jan 15 13:42:01 server dnsmasq[2974]: using nameserver 8.8.4.4#53
Jan 15 13:42:01 server systemd[1]: Started dnsmasq - A lightweight DHCP and caching DNS serve
```

I am running iptables, so I am not sure if that has something to do with it?

---

### Post by SeijiSensei on 2018-01-16
I always use isc-dhcp-server for this task.

You do need to make sure that ports 66 and 67 are open for UDP traffic to the interface the server is listening on.  Something like
```
/sbin/iptables -A INPUT -i eth1 -p udp --dport 67:68 -j ACCEPT
```

If you specify an IP address as well, it needs to be the all-ones broadcast address
```
/sbin/iptables -A INPUT -i eth1 -p udp -d 255.255.255.255 --dport 67:68 -j ACCEPT
```
to which all DHCP requests are directed.

---

