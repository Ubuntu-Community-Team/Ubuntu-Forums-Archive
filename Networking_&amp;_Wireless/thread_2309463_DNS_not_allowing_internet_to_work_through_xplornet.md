---
title: "DNS not allowing internet to work through xplornet"
date: 2016-01-10
forum: Networking &amp; Wireless
---

### Post by Elijah_Duffy on 2016-01-10
Recently we switched to xplornet from our local ISP, Okanagan Prewire. Immediately after the change, my laptop running Ubuntu 15.10 quit working on the internet. Previously, I had also noticed that my computer only worked on my home network if on Wi-Fi, and would only run through ethernet at other places such as the library. When I called xplorenet, they had me ping **8.8.8.8** (google), which worked. However, when I tried pinging [www.google.com](www.google.com), it didn't work. Likewise with my own website. The person I spoke to at xplornet told me that it was most likely a DNS issue since I have another fully functional Ubuntu computer, and that I needed to find out how to clear my DNS cache. So I searched around, finally ended installing **dnsmasq** (shouldn't that be preloaded on my computer?), clearing the dnsmasq cache, and restarting the **network-manager** service. I also tried adding **192.168.100.1** (xplornet modem) to the "Additional DNS Servers" setting. Still, nothing worked. When I reconnected to my old network, the internet worked just fine.

Since my old ISP is relatively slow in comparison to xplornet, I would greatly appreciate any help people here could give me. 

**COMPUTER / BROWSER INFORMATION:**
Ubuntu 15.10
e1000e Ethernet Driver
Lenovo ThinkPad T410
Firefox (not sure what version)

---

