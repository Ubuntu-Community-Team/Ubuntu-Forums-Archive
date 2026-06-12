---
title: "Wireless connection issue (WPA query loop)"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by konf300 on 2009-04-14
I have rtfm to install ndiswrapper and my wireless adapter driver is working just fine - at least I'm seeing "enable wireless" option when I right-click the NetworkManager and I can see a list of available routers when I left click on the tray icon.

I even managed to connect to my router the first time I had toyed around with NetworkManager and had internet connection for about 5 minutes (cue victory cry here). But then I lost connection and I've been in the dark ever since.

Now when I try to connect, I get a small popup window asking for WPA(personal) key. I enter my passphrase, the two dots on the systray start animating but it won't connect and about 1 minute later, I get the same popup window asking for WPA but this time when I click show my passphrase, I'll get what looks like an encrypted string. I have tried manually replacing it with my regular passphrase to no avail. I can't get out of this what I call a "WPA query loop". 

Please bear in mind that I had no WPA problems when I first installed ndiswrapper and connected to my wireless router.

My wireless modem/router is a USR9110. My wireless adapter is AirTies WUS-300 (usb stick). Ubuntu version 8.10.

Here is some info I've gathered after trying what seemed like an endless list of terminal commands:

```
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:3c:bd:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+tusb1150 driverversion=1.53
+Airties,06/01/2005,7.2.2.42 multicast=yes wireless=IEEE 802.11g

```


Also here's something from 192.168.2.1's Wireless Security settings:
```
Cypher suite: TKIP
Authentication: Pre-shared Key
Pre-shared key type: Passphrase	
Group Key Re-keying: disabled

```

All ideas are appreciated here.

---

### Post by konf300 on 2009-04-14
Now I've noticed NetworkManager is asking for WPA2, whereas my modem has a WPA passphrase. If anyone can provide me with the terminal command to assign a WPA passphrase to a SSID, I will report the outcome.

---

### Post by anewguy on 2009-04-14
Make sure you are selecting passkey or passphrase correctly.  I had that problem and it turned out I just hadn't selected the correct type of WPA and key/phrase type - it should be in a pull-down box on that window you get asking for the key.

I don't know if that's your problem, but the symptoms are very similar to what I had.  If worse comes to worse, use a cable and direct connect to the router and check it's settings, or even reset them to what you want, then try again.

Dave :)

---

