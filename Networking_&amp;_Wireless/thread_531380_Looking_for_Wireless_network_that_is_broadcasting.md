---
title: "Looking for Wireless network that is broadcasting"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by jubun2 on 2007-08-21
Hello, 
I am a linux newbie, i just installed Ubuntu 6.06.1.  It seems to have picked up both my wired and wireless nic cards, but I have not been able to determine how to search for Wireless networks that are broadcasting in the area.  Is there an easy way to see what WiFi Network are nearby?

---

### Post by spd106 on 2007-08-21
You should be able to see the ssids of local networks in the network-admin capplet (under System -> Admin -> Networking), see the drop down box.

You can also scan from a terminal using this command (assuming the interface is eth1).
```
sudo iwlist eth1 scan
```

If you want another graphical app that also supports WPA, then try installing Wifi-Radar or Network Manager from the universe repository through the Synaptic Package Manager.

---

### Post by jubun2 on 2007-08-23
Thank you, I don't see the APs in the Networking, but I installed Ubuntu on another laptop and it does show the APs there.  Thanks for the command syntax, I looked for the other tools you mentioned in the Synaptic package and don't see them under networking. Let me know if there is another location for these installs.

---

### Post by spd106 on 2007-08-23
There are better instructions here [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

To troubleshoot the wireless card follow the instructions on this page
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards)

---

