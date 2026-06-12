---
title: "Autoconnect to OpenVPN on startup"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by JazzPotato on 2014-10-29
Hi,
I'm connecting to an openVPN vpn server with network manager in Xubuntu14.04
I'd llike to configure my system to connect to this vpn at startup.
How would this be achieved?

---

### Post by The Cog on 2014-10-29
I think you place a suitable configuration file in /etc/openvpn. The filename must end in ".conf" e.g /etc/openvpn/my-vpn.conf . There is also a setting in /etc/default/openvpn where you can limit which .conf files are autostarted (the default is to start all /etc/openvpn/*.conf files).

---

### Post by Whoopie on 2014-10-29
Or you can use network-manager to connect to the VPN automatically. Just look into the settings in the 'General' tab.

---

### Post by JazzPotato on 2014-10-29
[ATTACH=CONFIG]257587[/ATTACH]
There is no option to automatically connect at startup in my "general" tab

---

### Post by Whoopie on 2014-10-29
Hmm, it's there under Ubuntu Trusty 14.04 under the settings for a wifi connection.

[ATTACH=CONFIG]257588[/ATTACH]

---

### Post by JazzPotato on 2014-10-29
My problem is now solved, it seems I was looking for the setting in the wrong place.
I was looking in the VPN settings when I should have been looking for the settings under the wifi connection.
Thank you very much for helping me :-)

---

