---
title: "wpa_supplicant and wireless network login at boot"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by Nicky_Boom on 2013-09-27
Hi everyone, 

I am trying to configure my Ubuntu 12.04 to automatically log in at boot on a wireless network using wpa-psk authentication. While I have no problem authenticating from the command prompt, I can't seem to make it work automatically during the startup phase.
I found many different suggested configurations available online, none of which work in my case. 

My wpa_supplicant.conf file looks like:

network={
        ssid="ADD-YOUR-SSID-HERE"
        psk="ADD-YOUR-WPA-PASSWORD-HERE"
}

while my /etc/network/interface file contains:



auto lo
iface lo inet loopback

auto eth0
iface eth0 inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-roam /etc/wpa_supplicant.conf


Do you have any suggestion about what might be wrong?

Cheers,

Nicky

---

### Post by praseodym on 2013-09-28
Check here:

[http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA2-Verschluesselung](http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA2-Verschluesselung)

which settings need to be written into the .conf file. You can also add the lines
```

        wpa-driver wext
        dns-nameservers x.x.x.x, y.y.y.y
```
to the "interfaces". If this is not enough add the lines

```
ifdown wlan0
ifup wlan0
```

before "exit 0" into the file **/etc/rc.local**
How does your /etc/resolv.conf look like?

---

