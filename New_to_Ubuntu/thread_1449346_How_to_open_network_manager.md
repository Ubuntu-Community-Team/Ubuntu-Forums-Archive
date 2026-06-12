---
title: "How to open network manager?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by servicetech on 2010-04-07
Trying to set up a wireless network and don't know the terminal command to start network manager. No GUI in the menu to select and run program.

RaLink RT2561/RT61 802.11g PCI

---

### Post by whoop on 2010-04-07
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Nascentes on 2010-04-07
Well, if you don't have a gui, then as far as I know, you need to use iwconfig to manually set your essid and security key.

```

iwconfig #find your wireless. Most commonly wlan0 I believe

iwconfig wlan0 essid <name of the network>

iwconfig wlan0 key <key of network>

man iwconfig #for more info

```

---

### Post by 2hot6ft2 on 2010-04-07
It's in the top right panel, not in the menu. Right click on it and select Edit Connections.

---

### Post by servicetech on 2010-04-07
How many bars are required for wireless to work properly?
The Ethernet icon goes in circles but never "connects"

---

