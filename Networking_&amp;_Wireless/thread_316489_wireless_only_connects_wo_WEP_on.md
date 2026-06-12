---
title: "wireless only connects w/o WEP on"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by dnljgrg on 2006-12-10
I've just installed Edgy Eft on Thursday and have been trying to get wireless working.  My coworker installed my drivers with ndiswrapper and the interface (ndktg - or what ever that's supposed to be called) and then I input the correct settings to connect to my router with WEP.  However, when I run iwconfig with the WEP on, my eth1 shows that it has a wireless connection, however the essid is labaled "off/any" or something like that.  I've checked /etc/network/interfaces and my ssid and password are correct, although sometimes I've seen a "s:" in front of my password and other times not.  So I turned off WEP on the router and set up wireless to just connect to my router and I can connect.  When I run iwconfig now, my essid shows correctly.  Any ideas why I can't connect?  Any certain things I should try?  Thanks.  -Dan

---

### Post by spd106 on 2006-12-11
I strongly suggest that you try it again with a hex based key. WEP is known to be less secure, but it's better than nothing. With a hex key you don't need to bother with the s:, so it is simpler and it's not like you have to enter it every day anyway.

---

### Post by YumaJim on 2006-12-11
Install and try 'wifi-radar'. I've had the best luck using it
to make wifi connections. All the other WiFi managers seem to have some problem that I had to fix by running a bash script. 'wifi-radar' is a gui interface that you can use to fully configure
you connection and the best part is it **works**.
YumaJim

---

### Post by dnljgrg on 2006-12-15
what worked for me was to enter the essid as xxxx-xxxx-xx as i read in some documentation.  also changed from open system to shared key.  i have no idea what that does but those two things together worked.  thanks for replying thought!

---

