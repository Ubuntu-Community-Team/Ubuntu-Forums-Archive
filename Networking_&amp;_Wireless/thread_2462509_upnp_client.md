---
title: "upnp client?"
date: 2021-05-22
forum: Networking &amp; Wireless
---

### Post by garlorsus on 2021-05-22
any upnp client for automated port forwarding?

I've got a rasp with a ssh and openvpn server, I want to be able to just connect it wherever and touch nothing from configuration if possible, to do this I'd need some automatic way for port forwarding, is there any type of upnp client where I can feed it the ports I want open and it does the upnp request to the ISP router?

all I can find on google about upnp client is to connect to media servers and see videos, so no much info there

---

### Post by TheFu on 2021-05-22
UPnP is a security nightmare.  [https://www.zdnet.com/article/how-to-fix-the-upnp-security-holes/](https://www.zdnet.com/article/how-to-fix-the-upnp-security-holes/)
Nobody thinks UPnP should be enabled on any routers today - well, except the vendors who make complex, multiple IP, interfaces to the world. For them, UPnP reduces support calls, especially from PUI gamers (playing under the influence).

If you want to open closed ports on a service, there is something called "port knocking", but it doesn't touch the WAN firewall.  Anything that did would be extremely specific to the router firmware.  Perhaps you could figure out how to initiate a login session with your WAN router, then determine the specific request to enable/disable the port forwarding.

What would be easier would be to use DHCP reservations based on the VPN server MAC.  Then when connected, it would always have the same static IP on the LAN and ports can be forwarded to the same LAN IP, since it was the same every time.  Just be certain the static IP is outside the dynamic DHCP range in the router configuration.  I do this for all devices on the home network that are a hassle to assign a static IP or if they need to be portable - so ... laptops and tablets and Roku and HDHR TV tuners get DHCP reserved IPs, but desktops and my raspberry-pis have static IPs configured.  I really don't want a failed DHCP server to prevent most of my systems from working fine.

---

### Post by garlorsus on 2021-05-22
TheFu, I don't care security, security in this instance on a scale of 1 to 10 is a -5, I just wanted a upnpc client, found it, port knocking requires some kind of configuration on the router

I answer myself
apt install miniupnpc
crontabe -e
*/60 * * * * upnpc -a 192.168.1.55 22 22 udp
*/60 * * * * upnpc -a 192.168.1.55 22 22 udp

---

