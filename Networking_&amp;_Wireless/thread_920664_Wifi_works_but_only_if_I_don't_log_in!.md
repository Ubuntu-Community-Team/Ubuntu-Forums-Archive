---
title: "Wifi works but only if I *don't* log in?!?"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by mcld on 2008-09-15
Hi - My DWL-G650+ wifi card was working fine but for some reason it is now not doing. When the computer boots, if I use the recovery menu to drop to a root prompt I can successfully connect to my wireless network:

 iwconfig wlan0 essid <the network name>
 iwconfig wlan0 ap <the code for the access point>
 iwconfig wlan0 key <the key>
 dhclient wlan0
 ping www.apple.com

...and ping works OK, so from the root prompt, things work fine. 

But if I then go and log in to the Xubuntu desktop like normal, and run exactly the **same** commands (with sudo), the "dhclient" command fails to get any external connectivity.

How can I find out what is breaking things? My wifi card clearly works so something is getting in the way after login.

---

### Post by mcld on 2008-09-15
OK, I think I might (?) have solved it, although I'm not sure why I need to do this.

I edited the file /etc/network/interfaces and filled in the details of my network (as described on [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) ), a bit like this:

```
 auto wlan0
 iface wlan0 inet dhcp
 wireless-key <the actual key>
 wireless-essid <the actual essid>
 wireless-mode managed
```

After reboot, it seems my system finds the network without problems, and web-browsing works etc etc. As I say, I'm not sure why I needed to do this, I already had the settings entered into the Network settings GUI. Maybe if you're in a similar situation you can try this!

---

