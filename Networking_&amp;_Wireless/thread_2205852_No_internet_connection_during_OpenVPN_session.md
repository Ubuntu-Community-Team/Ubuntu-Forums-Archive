---
title: "No internet connection during OpenVPN session"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by trym2 on 2014-02-16
Hi all, 

i've recently installed openvpn on my ubuntu server with the following guide : [https://www.digitalocean.com/community/articles/how-to-install-openvpn-access-server-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-openvpn-access-server-on-ubuntu-12-04), i'm however experiencing issues with the client as it connects but i cannot surf webpages while connected. Doing a research i came across with this: [http://ubuntuforums.org/showthread.php?t=2104379](http://ubuntuforums.org/showthread.php?t=2104379) . Ping test works fine , but in my openvpn control panel i cannot find ipv4 settings panel, may i have to do something on server side? 

thanks in advance

---

### Post by varunendra on 2014-02-16
Welcome to the forums trym2!

> **trym2 said:**
> Doing a research i came across with this: [http://ubuntuforums.org/showthread.php?t=2104379](http://ubuntuforums.org/showthread.php?t=2104379) . Ping test works fine , but in my openvpn control panel i cannot find ipv4 settings panel

The IPv4 tab they were discussing was the "IPv4 Settings" tab in Network Manager, not the VPN control panel. That is applicable to the client if it is using Ubuntu (GUI).

So, are you using Ubuntu (Desktop) on the client that is having this problem? If yes, apply the suggestion on its Network Manager settings for the VPN connection.

---

