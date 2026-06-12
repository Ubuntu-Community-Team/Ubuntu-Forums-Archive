---
title: "can't connect through winxp network bridge."
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by .chaos on 2008-06-23
i had this working friday now it's being a pain. new thread since the old one was about ICS and i'm no longer trying that as ICS doesn't want to setup for whatever reason.  keeps saying a machine is using a required IP.  to my knowledge the only required IP for ICS is 192.168.0.1 which nothing is on.  even my router is moved off.

so the new problem.  ```
/etc/init.d/networking restart
``` provides ```
RTNETLINK answers: no such process
```

after it says DHCPRELEASE to (Router IP) it says "There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072.

after that it tries DHCPDISCOVER on 255.255.255.255 (subnet is actually 255.0) port 67 and fails then sleeps. "No working leases in persistent database - sleeping" and drops me at the prompt.  says no DHCP offers received.  doesn't ping the router.

i tried using the graphic network manager to no avail. seems to edit the same /etc/network/interfaces file that i was editing manually anyway.

/etc/network/interfaces has the same exact info as my windows machine except the gateway address is the windows machine's address. i'm sharing the windows connection through a bridge.

i'm trying to set it up following this.

[http://www.nukesilo.com/2007/03/19/c...-ubuntu-linux/](http://www.nukesilo.com/2007/03/19/c...-ubuntu-linux/)

/etc/network/interfaces looks like this for my primary connection.  only other thing specified is the loopback which i didn't touch.

address = machine desired IP
netmask = subnet (255.255.255.0)
network = router IP (192.168.0.100)
broadcast = 192.168.0.255
gateway = XP machine 192.168.0.50
dns-nameservers = XP machine which is set to pull from the router which has DNS relay on.

it worked for like two days then saturday it went down and has stayed that way. seems to intermittently come and go until this where it finally died. never had an issue with it in windows even though it ran the same install for 5 years.

---

