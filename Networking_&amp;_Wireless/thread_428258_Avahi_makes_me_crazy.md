---
title: "Avahi makes me crazy"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by heepster on 2007-04-30
Hi
i have installed Kubuntu Feisty on my Laptop and I can't get avahi-daemon working correctly.
It starts on startup and it can resolve .local and browse MDNS but it ignores my avahi-daemon.conf, because it don't publish workstation or allows other apps to publish mdns. I can ping notebook.local from all my other computers and the other way round it also works.

But when i do a $ sudo /etc/init.d/avahi-daemon restart 
it works correct and publish workstation etc.

Here is the Log of avahi on boot:

```
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	avahi-daemon 0.6.17 starting up.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Interface eth0.IPv4 no longer relevant for mDNS.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Loading service file /services/ssh.service.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Network interface enumeration completed.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	New relevant interface eth0.IPv4 for mDNS.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Registering HINFO record with values 'I686'/'LINUX'.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Registering new address record for 192.168.200.20 on eth0.IPv4.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Registering new address record for fe80::20a:e4ff:fe00:9a3e on eth0.*.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Successfully called chroot().
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Successfully dropped remaining capabilities.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Successfully dropped root privileges.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Withdrawing address record for 192.168.200.20 on eth0.
30.04.2007 11:14:39	notebook	avahi-daemon[4717]	Withdrawing address record for fe80::20a:e4ff:fe00:9a3e on eth0.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Interface eth0.IPv4 no longer relevant for mDNS.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	New relevant interface eth0.IPv4 for mDNS.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	New relevant interface eth0.IPv4 for mDNS.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Registering new address record for 192.168.200.20 on eth0.IPv4.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Registering new address record for 192.168.200.20 on eth0.IPv4.
30.04.2007 11:14:43	notebook	avahi-daemon[4717]	Withdrawing address record for 192.168.200.20 on eth0.

```

Here is the log on restarting avahi;

```
30.04.2007 11:21:34	notebook	avahi-daemon[4717]	Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	avahi-daemon 0.6.17 starting up.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.200.20.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Loading service file /services/ssh.service.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Network interface enumeration completed.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	New relevant interface eth0.IPv4 for mDNS.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Registering HINFO record with values 'I686'/'LINUX'.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Registering new address record for 192.168.200.20 on eth0.IPv4.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Registering new address record for fe80::20a:e4ff:fe00:9a3e on eth0.*.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Successfully called chroot().
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Successfully dropped remaining capabilities.
30.04.2007 11:21:34	notebook	avahi-daemon[5659]	Successfully dropped root privileges.
30.04.2007 11:21:35	notebook	avahi-daemon[5659]	Server startup complete. Host name is notebook.local. Local service cookie is 1746685672.
30.04.2007 11:21:36	notebook	avahi-daemon[5659]	Service "Remote Terminal on notebook" (/services/ssh.service) successfully established.

```

And here is my avahi-daemon.conf
```

[server]
host-name=notebook
domain-name=local
#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=no
#check-response-ttl=no
#use-iff-running=no
#enable-dbus=yes
#disallow-other-stacks=no
#allow-point-to-point=no

[wide-area]
enable-wide-area=yes

[publish]
disable-publishing=no
disable-user-service-publishing=no
#add-service-cookie=yes
#publish-addresses=yes
#publish-hinfo=yes
publish-workstation=yes
publish-domain=yes
#publish-dns-servers=192.168.50.1, 192.168.50.2
#publish-resolv-conf-dns-servers=yes
#publish-aaaa-on-ipv4=yes
#publish-a-on-ipv6=no

[reflector]
#enable-reflector=no
#reflect-ipv=no

[rlimits]
#rlimit-as=
rlimit-core=0
rlimit-data=4194304
rlimit-fsize=0
rlimit-nofile=30
rlimit-stack=4194304
rlimit-nproc=3

```

BTW I've set /etc/default/avahi-daemon to 1

Sorry for bad english, I am from Germany

I hope anyone of you knows a solution..

---

### Post by heepster on 2007-05-01
No Idea

---

### Post by heepster on 2007-05-01
I've made a workaround for this, it's not very pretty but works for me.

Add /etc/avahi-daemon restart to /etc/rc.local

---

### Post by jfdill_2 on 2007-06-11
> **heepster said:**
> I've made a workaround for this, it's not very pretty but works for me.

Add /etc/avahi-daemon restart to /etc/rc.local

Did you check /etc/default/avahi-daemon to make sure AVAHI_DAEMON_START=1?  I don't know, I just started poking around with avahi, and found this doc in the wiki:

[https://help.ubuntu.com/community/HowToZeroconf?highlight=%28avahi%29](https://help.ubuntu.com/community/HowToZeroconf?highlight=%28avahi%29)

---

