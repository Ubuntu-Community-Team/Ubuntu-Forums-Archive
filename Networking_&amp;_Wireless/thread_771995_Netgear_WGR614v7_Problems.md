---
title: "Netgear WGR614v7 Problems"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by DoesThisNameWork on 2008-04-28
First of all I want to apologize if I missed something, I've read the stickies but to be honest I don't understand anything, as you already I'm not the most skilled person with these stuff.

I installed Ubuntu with wubi the newest version afaik. But it doesn't detect my WLAN Network, I can connect to the Internet with a cable but I don't got that option here. The routers distance between my computer is like 3 meters or something, I've got it enabled on roaming mode. I've read the help guides in the Ubuntu OS, but I'm like "öhh?" 

My router: Netgear WGR614v7
My NIC: Broadcom 802.11b/g WLAN

---

### Post by vanadium on 2008-04-28
The problem likely is not with the netgear. It probably is with your wireless USB stick or card (is that the Broadcom 802.11b/g WLAN?). Clicking the network icon, do you see your wireless network listed?

---

### Post by DoesThisNameWork on 2008-04-28
No, I don't see my network listed their, in fact I don't see any network, but from my windows I see 3 networks, which one of them are mine.

EDIT: Btw I use WPA-PSK [TKIP.

---

### Post by vanadium on 2008-04-28
Then it is surely your wireless card that is not supported. Many cards can be used using the windows drivers and a piece of software called "ndiswrapper", but it is hard to set that up. You should search for information on Ubuntu and your wireless device to see what solutions people had. Alternatively, you might consider purchasing a wireless USB that is supported by Ubuntu out of the box.

---

