---
title: "Problem with wpa_supplicant"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by lmandrake on 2006-08-14
Hello,

I'm trying to setup wpasupplicant with my AVM USB wireless stick. I followed the wiki howto WifiDocs/WPAHowTo and wpa is  partially working. When I start wpasupplicant and set the default gateway manually everything runs fine. But after a reboot or /etc/init.d/networking restart the wpasupplicant seens not to get started (/etc/network/if-pre-up.d/wpasupplicant should take care of that, right?). The ifconfig and iwconfig output looks fine so it must be wpasupplicant not being started and I don't want to add it to /etc/rc.local

/etc/network/interfaces:
```

iface wlan0 inet static
        pre-up ifconfig wlan0 up
        address 10.2.0.10
        netmask 255.255.255.0
        gateway 10.2.0.1
        wpa_conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0

```

/etc/default/wpasupplicant:
```

ENABLED=1
OPTIONS="-Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf"

```

There is no /etc/init.d/wpasupplicant (I've installed version 0.4.8-3ubuntu1.1)

Was there something in the wiki that I've overseen? And why is the gateway not set?

Thanks for your suggestions.

---

