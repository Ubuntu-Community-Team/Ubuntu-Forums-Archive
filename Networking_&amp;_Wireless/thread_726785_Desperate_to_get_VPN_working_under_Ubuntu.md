---
title: "Desperate to get VPN working under Ubuntu"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by larsdk on 2008-03-17
Hi,

I am sorry for posting this again, but I'm getting really desperate to get my VPN to work in Ubuntu so I can avoid having to reboot the machine if I need to work on a file from work. The problem with pptp-manager in the nm-applet seems to be that I have a static IP and because it was recommended, I installed KVpnc, but that does not work either (tells me "Remote modem has hung up. Connection was terminated"). It might be the firewall/iptables or it might be the configuration of KVpnc - I don't know. But what I do know is that I really need a working solution to this, so if anyone is willing to help me through whatever the issue might be here, I would be very, very thankful :)

Lars

---

### Post by enriquecm on 2008-03-17
apt-get install openvpn

---

### Post by larsdk on 2008-03-17
sorry - forgot to mention. The VPN at work i a microsoft pptp (in which case, I don't think openvpn will work?)

---

### Post by rgunn on 2008-03-17
pptp connections work for me using an ip address via dhcp in conjunction with the gnome network-manager. Did you try this or just go with a static address  ?

---

### Post by larsdk on 2008-03-17
but I have a static IP so how could I do that?

---

### Post by farahbod on 2008-03-24
larsdk sometimes ago, i was just like you. Reboot to Xp.
But currently i use my ubuntu to connect!
Here's what you need to do:

sudo apt-get install linux-pptp


You can also install pptpconfig which will help you to create the connection or create it by hand! I prefer the last! However give it a try, if fails let me know.


apt-get install pptpconfig


Now execute applications/other/pptpconfig and create a connection.

Most of the time, you have to set up routing information manually.
Use this or provide more information (ip addresses, etc.) so i can write the exact command

sudo route add default gw IPADDRESS


This way you send all your traffic to the peer ip address. you should issue that command after connection.

Hope be useful lars

---

