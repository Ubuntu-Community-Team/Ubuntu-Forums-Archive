---
title: "VPN conection over ubuntu 7.10"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by maoz3000 on 2007-11-12
Hi everyone!
Let me just say I am VERY new with ubuntu. I recenty installed the new version 7.10 and everything is working great. the only problem I still didnt manage is my VPN connection to my university... As I understood I should use the network manager and create new VPN, but I didnt find that option. I have also the link of the VPN instuctions given by the university, but offcourse, it is for windows systems only :(
[http://vpn.technion.ac.il/](http://vpn.technion.ac.il/) (maybe that can help, my network knowlege is really pour)

Does some one can give me any instructions how to set it up?
thanks!

---

### Post by zanglang on 2007-11-12
Your university seems to be using PPTP, so you'll need to install the 'network-manager-pptp' package (using apt-get, or install "VPN Connection Manager (PPP generic)" in Add/Remove software).

Afterwards, click the network manager icon, select "Configure VPN..." under VPN Connections in the drop down menu, and click Add. Finally, fill in 132.68.254.109 for the Gateway, give the connection a name and click Apply. You'll be able to connect to your vpn from the dropdown menu again. There might be screenshot visual guides for setting all this up, but you'll probably have to Google for it. Good luck. :P

---

