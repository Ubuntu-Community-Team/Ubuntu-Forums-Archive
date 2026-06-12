---
title: "Hotspot connection issues"
date: 2017-12-09
forum: Networking &amp; Wireless
---

### Post by vortexx74 on 2017-12-09
I have trouble to access to my Hotspot i created at Ubuntu Gnome 17.10 via iPhone
Trying to connect with the iPhone says "no internet connection available", and then nothing happens anymore.

Can't find out what is blocking

My Onboard WLAN Interface is: Intel Wireless 3165
Kernel: Linux Planet-X 4.13.0-19-generic #22-Ubuntu SMP Mon Dec 4 11:58:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
Loaded WLAN Driver: 
modinfo iwlwifi | grep 7260
firmware:       iwlwifi-7260-17.ucode

EDIT: Ok i found out that "dnsmasq" is blocking.
When i kill dnsmasq, i can connect but DNS resolving does not work. How can i adjust this?
> 
NetworkManager[3234]: dnsmasq: failed to create listening socket for 10.42.0.1: Die Adresse wird bereits verwendetNetworkManager[3234]: <warn>  [1512840518.1312] dnsmasq-manager: dnsmasq exited with error: Network access problem (address in use, permissions) (2)


Uninstalling dnsmasq solved the Problem for me.


[ATTACH]277783[/ATTACH]

---

