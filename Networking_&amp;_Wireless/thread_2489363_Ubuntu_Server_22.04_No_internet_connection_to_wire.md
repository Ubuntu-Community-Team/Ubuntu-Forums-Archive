---
title: "Ubuntu Server 22.04 No internet connection to wireless devices accessing via Gateway"
date: 2023-07-27
forum: Networking &amp; Wireless
---

### Post by bmstinton93 on 2023-07-27
[COLOR=#2A3C42][FONT=-apple-system]My situation. I have a Raspberry Pi with Ubuntu 22.04 server mode installed on it. I use this to run VPN's on and have the devices in my house pointing at the Ubuntu VM by changing the gateway to the ip of the pi. This has always worked perfectly in the format of no VPN switched on on the pi then I get my normal Internet connection through connected devices, with vpn on the pi I receive that vpn connection through the connected devices - perfect.[/FONT][/COLOR]
[COLOR=#2A3C42][FONT=-apple-system]However, recently, this has stopped working. I did upgrade my Amazon Eero 5 routers to Eero Pro 6's and that seems to be when it stopped working however I have tried removing these from the equation and plugging back in my virgin media router and it still doesn't work.[/FONT][/COLOR]
[COLOR=#2A3C42][FONT=-apple-system]The issue I'm having is - I connect a vpn on the pi and Internet works fine. Every device (Wired and wireless) with their gateway pointed at the pi works fine, gets the Internet per the VPN connection. However, if I switch this VPN off then my wireless connected devices no longer get an Internet connection, but weirdly the wired devices work fine. Doing a packet capture on this also seems to show the TCP retransmitting.[/FONT][/COLOR]

---

