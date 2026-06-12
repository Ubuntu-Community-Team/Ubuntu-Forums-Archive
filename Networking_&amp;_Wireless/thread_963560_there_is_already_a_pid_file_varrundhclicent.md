---
title: "there is already a pid file /var/run/dhclicent"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by ben22 on 2008-10-30
Hi,

I am using Hardy and cannot connect via ethernet card to the internet.

The interfaces file contains

```

atuo eth0
iface eth0 inet dhcp

```

When restarting the network with

```
sudo /etc/init.d/networking restart
```

It throws a message: 

```
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
```

then

```

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:13:8g:9gd2:dd
Sending on LPF/eth0/00:13:8g:9gd2:dd
Sending on Socket/fallback
DHCPDISCOVER on eht0 to 255.255.255.255 port 67 interval 4
...
No DHCPOFFERS received
No working leases in persistent database - sleeping.

```

Then it stops byiteslf the NTP server and restarts it
```

*Stopping NTP server ntpd
... done.
*Starting NTP server ntpd
... done.

```

My assumption is that there is something wrong with the pid file but don't really know how to continue from here.

thx for suggestions
Ben

---

### Post by ben22 on 2008-10-30
iwlist scan shows:

```
lo Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
wifi0  Interface doesn't support scanning.

ath0 Scan completed:
...
```

---

