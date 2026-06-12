---
title: "How I learned to stop worrying about wired issues and used a dhclient cronjob"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by roboa1983 on 2014-01-07
Hi,

About two weeks ago I suddenly started having internet connectivity problems using Ubuntu 13.04 (upgrading to Ubuntu 13.10 did not help). My card is a Realtek, and I am using a static IP, though I get the same problems if I switch to DHCP.

```
$ lspci -nn
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
```

I am currently using driver version 8169

Every time my syslog showed the following,
```
Jan  7 11:25:45 tulum avahi-daemon[802]: Invalid response packet from host 128...
Jan  7 11:25:45 tulum avahi-daemon[802]: Invalid response packet from host fe80...
Jan  7 11:25:48 tulum avahi-daemon[802]: Invalid response packet from host 128...
Jan  7 11:25:48 tulum avahi-daemon[802]: Invalid response packet from host fe80...
Jan  7 11:25:48 tulum avahi-daemon[802]: Invalid response packet from host 128...
Jan  7 11:26:21 tulum avahi-daemon[802]: Invalid response packet from host fe80...
Jan  7 11:26:21 tulum avahi-daemon[802]: Invalid response packet from host 128...
Jan  7 11:26:22 tulum avahi-daemon[802]: Invalid response packet from host fe80...
```

my internet connection would reset. This was about every three minutes. Other people in my office with ubuntu did not experience this.

The only workaround I could figure out is that using dhclient

```
sudo dhclient eth0
```

restored my internet connectivity, so I set a cronjob to run dhclient every three minutes.

```
$ sudo crontab -e 

*/3 * * * * * dhclient eth0
```

Of course this is just a hack, and I would like to get to the bottom of things (but currently do not have the time). So I just wanted to post this in case this is useful for someone else, and also in case someone has a better solution.

---

