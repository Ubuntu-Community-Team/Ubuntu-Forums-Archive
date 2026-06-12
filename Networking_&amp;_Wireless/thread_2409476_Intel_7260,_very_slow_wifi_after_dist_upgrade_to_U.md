---
title: "Intel 7260, very slow wifi after dist upgrade to Ubuntu 18.04"
date: 2019-01-02
forum: Networking &amp; Wireless
---

### Post by santiago-kuma on 2019-01-02
A couple of weeks ago I upgraded my system from 17.10 to 18.04 and after this I've noticed a very slow Wifi connection, mostly on the start up. Don't know exactly what's the problem; I've tried to ping google.com with no/very-few packet loss and I've also tried updating to google DNS.  
  
I've read the sticky and attached my wireless info below.

Thanks a lot for your help.

---

### Post by jbamford92 on 2019-01-02
> **santiago-kuma said:**
> A couple of weeks ago I upgraded my system from 17.10 to 18.04 and after this I've noticed a very slow Wifi connection, mostly on the start up. Don't know exactly what's the problem; I've tried to ping google.com with no/very-few packet loss and I've also tried updating to google DNS.  
  
I've read the sticky and attached my wireless info below.

Thanks a lot for your help.

I used the same WIFI Card in my Laptop. Be sure to disable DNSMASQ. Comment out dns=dnsmasq as DNS Forwarder can cause problems. You have also mentioned that you have tried different DNS Servers did you do this by editing /etc/network/interfaces?

---

### Post by santiago-kuma on 2019-01-02
Thank you for your quick response.

I was not sure on how to disable DNSMASQ so I followed a bunch of stack overflow threads. This is what I end up with:

/etc/systemd/resolved.conf
```

#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details

[Resolve]
DNS=8.8.8.8 2001:4860:4860::8888
FallbackDNS=8.8.4.4 2001:4860:4860::8844
#Domains=
#LLMNR=no
#MulticastDNS=no
DNSSEC=no
#Cache=yes
#DNSStubListener=no

```

/etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile
dns=default

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

```

Network seems better now, I'll try it out some time before marking it as solved. Thanks!!

---

### Post by chili555 on 2019-01-02
```
Cell 01 - Address: <MAC 'GABY' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"GABY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000058d1bfb195
                    Extra: Last beacon: 4472ms ago
                    IE: [COLOR="#FF0000"]WPA Version 1[/COLOR]
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get

```
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

---

### Post by jbamford92 on 2019-01-03
> **santiago-kuma said:**
> Thank you for your quick response.

I was not sure on how to disable DNSMASQ so I followed a bunch of stack overflow threads. This is what I end up with:

/etc/systemd/resolved.conf
```

#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details

[Resolve]
DNS=8.8.8.8 2001:4860:4860::8888
FallbackDNS=8.8.4.4 2001:4860:4860::8844
#Domains=
#LLMNR=no
#MulticastDNS=no
DNSSEC=no
#Cache=yes
#DNSStubListener=no

```

/etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile
dns=default

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

```

Network seems better now, I'll try it out some time before marking it as solved. Thanks!!


You need to comment out dns=default. Do not need to touch /etc/resolv.conf. One thing you didnt mention, how are you setting DNS? via /etc/network/interfaces?

/etc/NetworkManager/NetworkManager.conf

```

[main]
plugins=ifupdown,keyfile
#dns=default

[ifupdown]
managed=false

```

---

### Post by chili555 on 2019-01-03
> **jbamford92 said:**
> One thing you didnt mention, how are you setting DNS? via /etc/network/interfaces?Ubuntu 18.04 no longer uses /etc/network/interfaces; it uses netplan.

---

### Post by jbamford92 on 2019-01-06
> **chili555 said:**
> Ubuntu 18.04 no longer uses /etc/network/interfaces; it uses netplan.

Not true. If you use ifup or ifenslave then you use /etc/network/interfaces.

---

### Post by chili555 on 2019-01-06
> **jbamford92 said:**
> Not true. If you use ifup or ifenslave then you use /etc/network/interfaces.And you'd probably need to remove netplan and its yaml files, as well.

With enough modifications, you can do almost anything, including resisting inevitable change.

---

