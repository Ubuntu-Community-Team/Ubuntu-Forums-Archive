---
title: "wireless connection"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by mrcwine on 2010-02-18
wireless network not showing up with Ubuntu 9.10

---

### Post by NewbuntuUser777 on 2010-02-18
a specific network or no networks are showing up at all?

---

### Post by mrcwine on 2010-02-18
no network at all.

---

### Post by NewbuntuUser777 on 2010-02-18
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

"Open System > Preferences > Network Configuration - on Ubuntu 8.04 and 8.10 this should be System > Administration > Network. In 9.04 and 9.10 the information is found either by right clicking on the panel applet and selecting "Edit Connections" or in System > Preferences > Network Connections. If you can see an entry under the Wireless Connections tab, then you have a working connection already and simply need to activate it. Select the entry and click on the "Properties" button to the right. Check "Enable this connection" and fill in the appropriate information below (SSID, network name, passcode, and connection settings). When finished, click OK and wait for the system to activate your card. If this does not produce a working connection, make sure you have entered all settings correctly, then consult the remainder of this guide to track down your problem(s)."

---

### Post by mrcwine on 2010-02-18
If this does not produce a working connection, make sure you have entered all settings correctly, then consult the remainder of this guide to track down your problem(s).

No connections being shown

---

### Post by mrcwine on 2010-02-18
bump

---

### Post by mrcwine on 2010-02-18
How do I find what type of wireless card is in my old laptop?

---

### Post by iponeverything on 2010-02-18
sudo ```
lshw -c network
sudo lspci |grep -i network
```

---

### Post by mrcwine on 2010-02-18
I'm having a hard time with this step:

**If you get no output then the memory on the card cannot be read.** Now we need to open a configuration file and add this information to it: 
  gksudo gedit /etc/pcmcia/config.optsthe information you add should look like this, with your own data substituted. [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconExample48.png[/IMG] 
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"After making this change run this command:   sudo kill -HUP `cat /var/run/cardmgr.pid`

I think my memory card data is:

""Airconn", "INNPROCOMM IPN 2200", Wireless LAN Adapter (rev 01)

---

### Post by mrcwine on 2010-02-18
bump

---

### Post by mrcwine on 2010-02-19
bump

---

