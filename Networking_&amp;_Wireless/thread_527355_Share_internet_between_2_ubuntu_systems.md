---
title: "Share internet between 2 ubuntu systems"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by hexion on 2007-08-16
Hello.

Maybe this has been addressed before but I couldn't find any procedure that works here:

What I want is simple:
I have 2 systems, a desktop and a laptop. The desktop is connected to the internet by WIFI (wlan0).
Both are connected in a LAN.

What I want is the laptop to use the desktops connection to connect to the internet, so:

LAPTOP -> eth0 -> LAN_CABLE -> eth0 -> DESKTOP -> wlan0 -> INTERNET

How can I do it a simple way?
Note: I tried some howtos such as this: [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html) but no results..

Thanks

---

### Post by tbfr on 2007-08-16
Did you try Firestarter on your Desktop already?

[http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing]("http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing")

---

### Post by hexion on 2007-08-16
Yes, I tried but with no results :(

My WLAN's net is 192.168.0.X, so I configured the desktop's LAN interface card to be 172.16.0.1

I actived the internet sharing in firestarter between eth1 and eth0, started the firewall, and set the laptops IP to 172.16.0.xx and its "router address" (don't remember the word in english) to 172.16.0.1

But I cannot even ping the desktop from the laptop :(
Any ideas?

---

