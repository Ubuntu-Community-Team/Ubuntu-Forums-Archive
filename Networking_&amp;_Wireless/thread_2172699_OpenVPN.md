---
title: "OpenVPN"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by davaweb on 2013-09-06
Hi
Ubuntu 12.04 classic
openvpn using network manager

I have been asked by my vpn provider to disable the TAP/TUN Adapter and then re-enable it again.

1)  How do I do this please?
2)  Are there any files that would cause the problems I have:
     a)  my ip address is NOT changed when using one particular VPN connection
     b)  I am unable to connect to some of their VPN sites but should be able to.

3) When I 'nmcli con list | grep -i vpn' how does the uuid relate to the VPN IP address and why does a uuid change if I haven't changed the VPN setting?

Many thanks
david

---

### Post by prodigy_ on 2013-09-06
TAP and TUN "adapters" are virtual devices that are automatically created for certain types of connections. I guess you only need to disconnect and re-connect.

---

### Post by davaweb on 2013-09-06
Thanks prodigy[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=518500")

---

