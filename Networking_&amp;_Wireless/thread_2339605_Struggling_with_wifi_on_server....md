---
title: "Struggling with wifi on server..."
date: 2016-10-10
forum: Networking &amp; Wireless
---

### Post by tsouza on 2016-10-10
Hello,

I have tried everything, but I simply can not get wifi working on my server. When I run "ifup -v wlp2s0" I get the following:

Note: An interesting fact is that while installing Ubuntu, wifi worked without any issues. I also have several other devices connected using dhcp.

```

Parsing file /etc/network/interfaces.d/wlp2s0
Configuring interface wlp2s0=wlp2s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /run/wpa_supplicant.wlp2s0.pid -i wlp2s0 -D nl80211,wext -C /run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlp2s0.pid
wpa_supplicant: ctrl_interface socket located at /run/wpa_supplicant/wlp2s0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "costasouza-5ghz" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

/sbin/dhclient -1 -v -pf /run/dhclient.wlp2s0.pid -lf /var/lib/dhcp/dhclient.wlp2s0.leases -I -df /var/lib/dhcp/dhclient6.wlp2s0.leases wlp2s0 	
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/c4:d9:87:3a:b1:41
Sending on   LPF/wlp2s0/c4:d9:87:3a:b1:41
Sending on   Socket/fallback
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 4 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 13 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 11 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 7 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 8 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 21 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 14 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 17 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 14 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 15 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 14 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 8 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 15 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 11 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 18 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 11 (xid=0x8f150124)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x8f150124)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

I also have a wired connection that is enabled now. It wasn't plugged in while installing Ubuntu.

The output of iwconfig is:
```

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Here is my setup:

OS: Ubuntu Server 16.04.1
Hardware: Intel NUC DC3217BY
NIC: Intel Corporation Centrino Advanced-N 6235 (rev 24)

Interface shows as wlp2s0 and I have configured /etc/interfaces.d/wlp2s0 with the following:
```

auto wlp2s0
iface wlp2s0 inet dhcp
  wpa-ssid costasouza-5ghz
  wpa-psk *****

```

Where ***** is my wifi password. I have used both clear text password and also generated by wpa_passphrase. Both types I get the same error.

When trying static ip, I don't get the DHCP messages, but wifi still does not works (shows the same output of iwconfig).

Any clue anyone???

Thanks!!!!

---

### Post by tsouza on 2016-10-10
Ok, I figured it out. It was a small stupid typo in ssid, sorry for the noise..

---

