---
title: "Intel Corporation Wireless 3165 random disconnect - Xubuntu 18.10"
date: 2019-01-14
forum: Networking &amp; Wireless
---

### Post by mato848 on 2019-01-14
Hi, 
I get randomly disconnected from my wifi.  Network manager shows that i am still connected, but network traffic stops.
I have tried several  workarounds but none helped. 
I would be happy if someone could help me to troubleshoot this. Thank you :) 


My wireless info is in attachment

---

### Post by jeremy31 on 2019-01-14
See if it happens after ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
That will keep Network Manager from enabling wifi power management

---

### Post by mato848 on 2019-01-14
Yes, it still happens. 
Are there some logs i could view when this happens ?

---

### Post by jeremy31 on 2019-01-14
You could run the following command in terminal and see what is going on when the issue occurs
```
tail -f /var/log/syslog
```
It might be the result of having the wifi router on auto channel and auto 20/40 MHz bandwidth

---

### Post by mato848 on 2019-01-14
Nothing happens in syslog when i get disconnected. Also aj have already set the channel and bandwidth on router so it is not changing :(

my syslog: 
```

Jan 14 23:35:15 benq systemd[1]: Startup finished in 5.310s (firmware) + 4.416s (loader) + 1.860s (kernel) + 7.203s (userspace) = 18.790s.
Jan 14 23:35:15 benq whoopsie[1660]: [23:35:15] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Jan 14 23:35:15 benq whoopsie[1660]: [23:35:15] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Jan 14 23:35:15 benq whoopsie[1660]: [23:35:15] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Jan 14 23:35:15 benq avahi-daemon[585]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::e54:15ff:fea3:7cbc.
Jan 14 23:35:15 benq avahi-daemon[585]: New relevant interface wlp3s0.IPv6 for mDNS.
Jan 14 23:35:15 benq avahi-daemon[585]: Registering new address record for fe80::e54:15ff:fea3:7cbc on wlp3s0.*.
Jan 14 23:35:15 benq NetworkManager[557]: <info>  [1547505315.6351] policy: set 'Domace' (wlp3s0) as default for IPv6 routing and DNS
Jan 14 23:35:39 benq systemd-timesyncd[481]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).
Jan 14 23:35:44 benq blueman-mechanism: Exiting 

```

---

