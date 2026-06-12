---
title: "Can this be done in /etc/network/interfaces ?"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by AVT- on 2008-06-19
Well, AP mode is now working for me, however, I can't seem to figure out how to get it to work on startup, so, I'm wondering, do I need to do more than edit /etc/network/interfaces which looks like this ATM:

> #wifi
auto ath0
iface ath0 inet manual
pre-up wlanconfig ath0 destroy
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
wireless-mode master
wireless-essid avtnetwork
wireless-channel 11
post-up /etc/init.d/hostapd -d /etc/hostapd/hostapd.conf

Am I doing something wrong? I can get everything working by running the following in terminal:

> 
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode ap
brctl addif br0 ath0
iwconfig ath0 essid avtnetwork
iwconfig ath0 channel 11
/etc/init.d/hostapd -dd /etc/hostapd/hostapd.conf


On a side note, my system sometimes randomly locks while running these commands.

Anyway, how would I setup /etc/network/interfaces? Or would I need to setup something else?

---

### Post by JanCeuleers on 2008-07-13
Two hints:

At pre-up time the ath0 interface does not necessarily exist. Best "post-down wlanconfig ath0 destroy" instead.

The hostapd script in /etc/init.d needs to be called differently. You need something like "post-up /etc/init.d/hostapd start".

Mine looks like this:

```
iface ath0 inet static
        address 192.168.15.1
        netmask 255.255.255.0
        broadcast 192.168.15.255
        network 192.168.15.0
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
        wireless-essid "Test"
        wireless-rate 54Mb
        wireless txpower auto
        post-up /etc/init.d/hostapd start
        down /etc/init.d/hostapd stop
        post-down wlanconfig ath0 destroy
```

Cheers, Jan

---

### Post by AVT- on 2008-07-23
> **JanCeuleers said:**
> Two hints:

At pre-up time the ath0 interface does not necessarily exist. Best "post-down wlanconfig ath0 destroy" instead.

The hostapd script in /etc/init.d needs to be called differently. You need something like "post-up /etc/init.d/hostapd start".

Mine looks like this:

```
iface ath0 inet static
        address 192.168.15.1
        netmask 255.255.255.0
        broadcast 192.168.15.255
        network 192.168.15.0
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
        wireless-essid "Test"
        wireless-rate 54Mb
        wireless txpower auto
        post-up /etc/init.d/hostapd start
        down /etc/init.d/hostapd stop
        post-down wlanconfig ath0 destroy
```

Cheers, Jan

Firstly, thanks for the help!

I can't use /etc/init.d/hostapd start or /etc/init.d/hostapd stop because it errors:

Configuration file: stop
Could not open configuration file 'stop' for reading.

But at least I'm getting somewhere.

edit5:

#wifi
iface ath0 inet static
address 192.168.15.1
netmask 255.255.255.0
pre-up wlanconfig ath0 destroy
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
wireless-essid avtnetwork
up brctl addif br0 ath0
post-up /etc/init.d/hostapd -d /etc/hostapd/hostapd.conf

Does not work on startup. But works if I run ifup ath0.

---

