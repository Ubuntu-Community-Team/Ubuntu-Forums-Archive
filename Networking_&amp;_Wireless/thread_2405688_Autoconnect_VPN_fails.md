---
title: "Autoconnect VPN fails"
date: 2018-11-09
forum: Networking &amp; Wireless
---

### Post by pingaan on 2018-11-09
Hi,

Short story. I recently installed 18.04 and I am enjoying a lot, I have setup my PC to automatically connect to my VPN provider on each startup and each time I return from suspend. Worked flawlessly.
A few days ago I changed VPN provider and replaced the old connection with the new and now it fails each time I boot up or return from sleep.
It fails as in not connecting to the wifi all together. I can manually connect to the WiFi and when I do that the VPN connects as well. Also if I prevent the VPN autoconnection the WiFi reconnects without any issues.

The "failed to connect to VPN" notification shows 4-5 times before it stops the connection tries all together. It's kind of like the VPN connection trying to connect before there is a connection to the internet, thus preventing the whole connection process.

I am using nm-connection-editor to sort out the VPN autoconnection and the VPN service, itself, is openvpn, which I setup using the "network-manager-openvpn-gnome" package. 

Is there a way I can record a log on what happens, so that someone may be able to help out?

Thanks!

---

### Post by pingaan on 2018-11-09
Update: I just noticed that when not connecting to a WiFi after rebooting I turned off the VPN autoconnection using nm-connection-editor and the computer connects to the WiFi instantly. It must be nm-connection-editor that's causing the issues.

---

### Post by kylar-stern on 2019-05-07
Did you ever manage to get this working?

I'm getting this same issue however with a wired Ethernet connection. I have set my network to connect to the VPN automatically using nm-connection-editor after which my network no longer automatically connect when i boot. I can connect to it manually and VPN also automatically connect when i do this. Just cant get the main network to auto connect.\

Running v19.04

---

### Post by PC_Dude74 on 2019-05-29
I'm having the same issues using the nm-connection-editor. I'm connected via the ethernet port and have set my VPN to automatically connect. But after reboot the ethernet connection and VPN are turned off. When I manually turned the ethernet connection on, the VPN turns on with it. Just wish I could fix this issue. Anyone have any ideas?

---

