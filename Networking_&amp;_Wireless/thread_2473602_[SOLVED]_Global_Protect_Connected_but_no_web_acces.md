---
title: "[SOLVED] Global Protect Connected but no web access"
date: 2022-04-08
forum: Networking &amp; Wireless
---

### Post by cgosorio on 2022-04-08
[COLOR=#3E3E3E][FONT=Lato]I am experimenting a very strange behavior with Global Protect (from Palo Alto) when connecting to my work VPN from my home WiFi. I am able to connect to the VPN of my work and even doing ssh to the server in the private network, but when I try to surf the web, the browser does not show anything. When I disconnect from the VPN, I am not able to connect to the server anymore (as expected) and I able to access the web. This happens in a linux machine with Ubuntu 20.04.4 LTS and firewall disconnected. At the beginning I thought it was something to do with my ISP, but I have tried with another machine with Debian 11.3, and there using the Global Protect client I can connect the VPN and access the web and the servers via ssh. Also in a Mac machine I can connect the VPN and ssh and surf the web afterwards. So my bet now is that it is a problem with Ubuntu. Is anybody using Global Protect in Ubuntu and experimenting this kind of behavior? Any solution or suggestion that can help to identify the cause of this behavior?[/FONT][/COLOR]

---

### Post by cgosorio on 2022-04-08
I have been able to solve the issue myself. Apparently the problem is due to the GlobalProtect script unable to change /etc/resolv.conf. So after connecting to the VPN the DNS address there were not changed to point to the DNS inside the organization. Now, I have a couple of scripts, one to connect, one to disconnect, that manage the connection and the change of /etc/resolv.conf.

---

### Post by drfox on 2022-05-18
I am getting this error when I connect to GlobalProtect after it sends me a push to Duo and I confirm:
Failed to load URL [https://(TheURLthatWorksinWindows)/SAML20/SP/ACS](https://(TheURLthatWorksinWindows)/SAML20/SP/ACS)
Do you have any idea what I need to do to solve the problem?
Thanks

---

