---
title: "install a VPN server that only use username and password"
date: 2021-07-20
forum: Networking &amp; Wireless
---

### Post by cazz on 2021-07-20
Hi
I was thinking about install a VPN server on ubuntu server 20.04.
I have install one time before OpenVPN but that was a long time ago and it did work but was not so easy to use because I need to export and import cert on client I going to use.
So after a time I did buy a hardware VPN that only use username and password.

But now is time that I install VPN at a friend and I wonder does OpenVPN or Wireguard support for only use username and password?
Or maybe some else VPN server that have support for that?
I know PPTP have it but is not so secure anymore what I know so I don't like to use it.

---

### Post by TheFu on 2021-07-22
> **cazz said:**
>  
But now is time that I install VPN at a friend and I wonder does OpenVPN or Wireguard support for only use username and password?


Nope.  Passwords alone are considered a security failure.  [https://www.bcs.org/content-hub/passwords-a-lesson-in-cyber-security-failure/](https://www.bcs.org/content-hub/passwords-a-lesson-in-cyber-security-failure/)

Commercial OpenVPN uses both keys AND userid/passwords.  The paid version of OpenVPN will generate a QR-Code to help devices "import" the client key and settings.  Also, 2FA is possible for greater security.  The idea of less security sorta defeats the purpose for using a VPN.

Wireguard will use QR-codes too: [https://serversideup.net/generating-wireguard-qr-codes-for-fast-mobile-deployments/](https://serversideup.net/generating-wireguard-qr-codes-for-fast-mobile-deployments/)  I've used this. It was very easy for Android devices.  For real computers, I just used my password manager to transfer the client config file for each client.  In my setup, each client has a different key, gets a different static IP on the VPN subnet and gets access to different LANs based on which client config is used. My android devices get to read-only media files and a few web servers like nextcloud, wallabag, calibre.  My personal key for my laptop can get to any LAN in my home - servers, desktops, games and IoS LANs.  [https://github.com/angristan/wireguard-install](https://github.com/angristan/wireguard-install) is an example setup. I didn't use this.

The really security-minded person would go with an IPSec VPN. These are a hassle.  I've never run one on Linux, but was part of a team that deployed one into an enterprise for 25K employees long ago using 2FA. Honestly, it was mostly a hardware-based solution integrated and validated by a huge telecom equipment vendor. I think FreeSWAN or LibreSWAN [s]or StrongSWAN[/s] are the Linux IPSec implementations.  iOS has an IPSec implementation compatible with these built-into the OS.  [https://github.com/hwdsl2/setup-ipsec-vpn](https://github.com/hwdsl2/setup-ipsec-vpn) is an example setup. I didn't use this. There are both PSK, userids and passwords.

There are lots of scripted VPN setup guides on github.  

If you want easy and don't care about security, look for a proxy server, not a VPN.  These days, *ms-pptp* is effectively a proxy server with zero security. The protocol was cracked in 2005 and hasn't been recommended for use since then.

---

