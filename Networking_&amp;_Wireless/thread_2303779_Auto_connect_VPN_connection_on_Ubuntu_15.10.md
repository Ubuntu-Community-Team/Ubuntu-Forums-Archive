---
title: "Auto connect VPN connection on Ubuntu 15.10"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by aurel130492 on 2015-11-21
Hi all,

I've migrated on Ubuntu 15.10, it's ok but my VPN connection doesn't connect automatically on boot. 
This script worked good on Ubuntu 15.04 and now, doesn't work ...

In /etc/NetworkManager/dispatcher.d, my script name 02vpn

```

[FONT=Ubuntu]#!/bin/bash[/FONT]
CON_NAME="enp2s0"
VPN_NAME="CyberGhost-CzechRepublic"

CON_STAT=$(nmcli con show --active | grep "${CON_NAME}")
VPN_STAT=$(nmcli con show --active | grep "${VPN_NAME}")

if [ ! -z "${CON_STAT}" -a -z "${VPN_STAT}" ]; then

    nmcli con up id "${VPN_NAME}"
 [FONT=Ubuntu]fi[/FONT]
```

When I execute the script with command line "/etc/NetworkManager/dispatched.d/02vpn", it's works. But doesn't on boot ...
I try to activate my script with the "Boot Application" but no success ...

Why my script doesn't works ? How can I connect my VPN on boot ?

Thanks you in advance and sorry for my approximative english :)

---

### Post by adagio on 2015-11-21
There are a number of 'connect-*' openvpn config. options, particularly connect-retry and related options, have solved similar issues in the past for myself.

---

### Post by adagio on 2015-11-22
Having said that that is assuming enp2s0 is actually up and running at that point (i.e., in the boot sequence).

---

### Post by aurel130492 on 2015-11-22
yes, the enp2s0 is up automatically on boot and normally, before the script. 

There isn't this option "connect retry" in "Advanced settings" of my VPN connection :/.

How I can see if the script is executing before my connection ?

---

### Post by aurel130492 on 2015-11-23
Hi,

I just saw my VPN connection sometimes cut and I must reconnect manually ...

---

### Post by aurel130492 on 2015-11-29
Anyone can help me please ? :(

Anyone use a VPN with automatic connection on Ubuntu 15.10 ? :(

---

### Post by dave205 on 2015-12-26
this is a great question I'm researching myself!  I'm going to try with the upstart daemon.

---

### Post by dave205 on 2015-12-28
> **aurel130492 said:**
> Anyone can help me please ? :(

Anyone use a VPN with automatic connection on Ubuntu 15.10 ? :(


Yes! I found in the network configuration manager, for your wireless config you are using (not the vpn connection but the wireless connection), select the General tab and you will find a "automatically connect to a vpn connection when using this connection" option. If you select that, next time you boot your computer, before you even log in you will be prompted for the vpn password. Personally I would rather it not connect at all until I log in but then in this case I am using this as a desktop and not a server.

---

