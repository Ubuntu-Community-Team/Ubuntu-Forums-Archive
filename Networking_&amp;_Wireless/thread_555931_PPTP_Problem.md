---
title: "PPTP Problem"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by badseed on 2007-09-20
Hi,
I'm using 7.04.
On my company we have a wireless network that as a wpa key to connect with and then I have to make a PPTP connection to the wireless appliance, I've installed the network-manager-pptp and made the connection ok.

The problem is that after 1 or 2 minutes the connection pptp is dropped (the interface just desapears from the list) even if I'm doing a continuous ping to a known host.

Can anyone help me

Thanks
João Mendes

---

### Post by stefan.ohsiek on 2007-09-21
I am afraid what you are trying to do, is not really supported in network manager. see [http://kutuma.blogspot.com/2007/05/vpn-to-windows-network-in-ubuntu.html]("http://kutuma.blogspot.com/2007/05/vpn-to-windows-network-in-ubuntu.html")

Apart from that PPTP VPN is very sensitive to its connection environment. I use it on a daily basis to my office and customers and I use a fixed DSL line and on a bad day I may get a disconnection every 10 minutes. It is not the best type of VPN but it is the most commonly used and easy to set up VPN around. And because of that we put up with the limitations.   

My suggestion to you would be to get a fixed connection like DSL for your PPTP purposes. Wireless is going to frustrate you endlessly.

---

