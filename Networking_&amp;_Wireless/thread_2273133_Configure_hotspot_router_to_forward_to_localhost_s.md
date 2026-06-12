---
title: "Configure hotspot router to forward to localhost server?"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by hillboy2 on 2015-04-10
[COLOR=#111111][FONT=Ubuntu]I have hostapd and isc-dhcp-server working on my linux 14.04 box. My WiFi devices can find the hotspot and are assigned an ipaddress. At this point there is no connection through to eth0.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I also have a nodejs servers on localhost port 23 and port 80. How do I get all requests coming in on the WiFi to be sent to localhost. My network will all be local and not connected to the www. I assume it's an item in /etc/dhcp/dhcpd.conf but I'm not up to speed with subnet mask configuration.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I wanted to allow certain domain requests to be forwarded to the outside world over eth0 how would that be done? [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I know that some WiFi Routers throw up a local html page to get people to log in before they can get access to www. How is that accomplished?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Maybe you know where I should look for help?[/FONT][/COLOR]

---

