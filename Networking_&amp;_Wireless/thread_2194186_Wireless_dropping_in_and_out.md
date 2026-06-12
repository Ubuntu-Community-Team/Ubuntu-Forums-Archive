---
title: "Wireless dropping in and out"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by meade1635 on 2013-12-16
I'm very new at this so please take it easy on me. I also see several posts asking questions similar to mine, but I'm having trouble understanding all the information I see.

With that said, here it goes.

Today I installed Ubuntu 12.04 on my laptop. It's an HP Pavilion dv6 ... Everything is good, except for the wirless connection. The Wifi just goes in and out and keeps asking me for authenication after a few minutes of use. While it is connected to Wifi, it is very slow. I connected using an Ethernet cable, and it is fast and has no problems. Can anyone help me? If you take a crack at it, please try to make it something I can understand.

Thank you!

---

### Post by alankon on 2013-12-17
Hi,

I had the same problem recently... after some research I realised the problem was with my wifi router, rather than with Ubuntu itself (I have a Belkin Surf N300 (be interesting to know if it's the same router?)).

I fixed it by going to the router's set-up page (192.168.2.1) [note: I actually did this using a windows machine that held a stable wifi connection, but I guess you could use your ethernet cable if you don't have this option], navigate to the "wireless" section, and you should see two options: "Wireless Channel" and "Extension Channel" both set to "Auto"?

If you change "Wireless Channel" to "6" and "Extension Channel" to "2", then restart your router... then try booting Ubuntu on wifi and with any luck you'll have a stable wifi connection.

---

### Post by meade1635 on 2013-12-18
Sorry for the slow response. I actually found a short YouTube video that suggested something I had not thought of. It said to uninstall Ubuntu, connect the computer using an Ethernet cable, then reinstall Ubuntu. I don't know why it worked differently than just installing and then connecting to WiFi for the updates, but it did. My WiFi connection is strong and fast. Working like a champ!

---

