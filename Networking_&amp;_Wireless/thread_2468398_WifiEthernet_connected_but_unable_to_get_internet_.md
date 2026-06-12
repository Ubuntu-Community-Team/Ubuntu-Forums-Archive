---
title: "Wifi/Ethernet connected but unable to get internet connection 20.0.4.3"
date: 2021-10-28
forum: Networking &amp; Wireless
---

### Post by rhynotr on 2021-10-28
I am brand new to Linux and I have Ubuntu 20.04.3 installed on my Mac Air 2013. At first I was able to get internet through wireless internet connection, but that soon failed. I did research and saw that I needed to connect my Network card (BCM4360 802.11ac) by going into the software update area in the settings. I connected that and it worked.

It stopped working although my network card was still connected. I read countless forums and looked over problems that were similar to mine and tried different solutions. 

I also connected a wired Ethernet to the back of my router and it showed connected, but the internet still didn’t work.
I pinged my router: 10.0.0.1 and 8.8.8.8 to which it was successful. I then attempted to ping google.com and it didn’t work. Nothing outside of my LAN worked.

This is the information I collected from my system:

---

### Post by TheFu on 2021-10-28
All questions related to Apple hardware should probably be asked in the Apple User's subforum.  Apple stuff tends to be "weird".
Also, whenever posting here, please copy/paste the text, not images.  500 bytes vs 10KB and people with eyesight issues can help.

If you can ping 8.8.8.8 - then the networking is fine.  **You have a DNS issue.**  Fix that.
Also, never have both the ethernet and wifi connections active concurrently when you are new. Bad things happen.

---

### Post by grahammechanical on 2021-10-28
If the WiFi network card and the Ethernet network card are connected to the router/hub but you do not have an internet connection, then the problem could be that the router/hub is not connected to an Internet Service Provider (ISP).

Land line internet connections can fail if there is noise on the telephone line. As I know only to well. If the router is switched on after the OS has been loaded, then the OS will connect to the router but there will be no internet connection because the router has not connected to the ISP. This happens to me and I use a web browser to access the router's setup utility and I check that the router is connected to the ISP and If not I activate a connection.

You will need to read any information provided by the supplier of the router/hub to find out how to access the router/hub setup utility.

Regards

---

### Post by praseodym on 2021-10-30
SecureBoot is disabled?

---

### Post by chili555 on 2021-10-30
What does this tell us?

```
ls -al /etc/resolv.conf
```

---

