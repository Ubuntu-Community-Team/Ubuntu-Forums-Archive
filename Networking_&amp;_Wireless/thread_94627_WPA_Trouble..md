---
title: "WPA Trouble."
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by PPower on 2005-11-24
(Technicaly this is not related to hardware but it is related to networking so I think this is the right place to put it :-))

I need a way to get wpa_supplicant to load upon bootup, just at the right time. There does not seem to be a simple way to do this and I know no way to make a init script. I need wpa_supplicant to run straight after ifconfig wlan0 up is ran and it needs to be ran this way: wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw

If someone could help I would be very greatfull. Thanks in advance :smile:

---

### Post by Rob2687 on 2005-11-24
You can edit the /etc/network/interfaces file and put:

```
auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

This will start wpa_supplicant and attempt to connect with dhcp at boot. I'm not sure how to change it to just start wpa though.

---

### Post by PPower on 2005-11-24
[QUOTE=Rob2687]You can edit the /etc/network/interfaces file and put:

```
auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

This will start wpa_supplicant and attempt to connect with dhcp at boot. I'm not sure how to change it to just start wpa though.[/QUOTE]
Thanks! It worked. wpa_supplicant did everything. Now do you know how to stop wpa_supplicant from loading at the end of bootup because of the way the deb was configured. Really I think a debconf question should be created for this.

---

