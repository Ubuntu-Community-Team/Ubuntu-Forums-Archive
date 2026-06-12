---
title: "VNC via wlan"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by therock003 on 2008-06-11
How can i set ubuntu and have vnc and at the some time have access wirelessly from another device and see from there what's happening on my ubuntu desktop?

---

### Post by pytheas22 on 2008-06-11
Provided your Ubuntu system has a working wireless card, you just need to go to System>Preferences>Remote Desktop to enable vnc.  Then connect to Ubuntu via vnc from wherever you want.  If you need to know the IP address of your Ubuntu machine, type "ifconfig" in a terminal.  Note that if there's a proxy server or router between your Ubuntu computer and the Internet, you'll have to set up port forwarding on the router in order to remote into Ubuntu from the Internet.

---

### Post by superprash2003 on 2008-06-11
more details would help.. do you want to access your ubuntu desktop from a ubuntu pc or a windows pc? via LAN or from the internet?

---

### Post by therock003 on 2008-06-12
I want to access it from my mobile device (nokia n93i),which since its symbian it does support installation of a couple of vnc applications,and via lan,not the internet.

The local ip of any given computer corresponds to a network no matter if its lan or wlan?I mean if local ip is 10.0.0.1 it's the smae even if you want to communicate with a cable or wirellessly?

Any additional info i should be aware of?

---

### Post by pytheas22 on 2008-06-12
> The local ip of any given computer corresponds to a network no matter if its lan or wlan?

Yes, unless your network is set up in a strange way, this is the way it works.  As long as both devices on on the internal LAN/WLAN, you just need to use local IP addresses to connect.

Keep in mind that if you're using dhcp, the local IP address assigned to your Ubuntu computer might not always be the same by default.  You can probably configure your router to always assign the same one, however.

---

