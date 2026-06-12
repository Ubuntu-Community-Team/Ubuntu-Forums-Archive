---
title: "Setting a fixed IP with NetworkManager"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by zapcome on 2006-11-01
Is there a way to have a fixed network configuration for a wireless network using NetworkManager?...

When Im at home, I wanna use a fixed IP and my own DNS servers, not the ones that NetworkManager sets... but it seems that this is not possible using NetworkManager - or at least the NetworkManager GUI.

How can I do this?

---

### Post by wieman01 on 2006-11-01
You can't. NetworkManager currently only allows for DHCP.

The only option for you is a tool called "Wifi-Radar" or a manual approach which basically entails editing "/etc/network/interfaces" as described in here: [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

---

### Post by jpkotta on 2006-11-01
I don't know about how to do it in network manager, but you can do it in network-admin.  I keep network settings for home and school separate this way.

Set the settings how you want.  Then go to the top bar of the gui and do an "create location".  Repeat for each location.

You can request a fixed IP address by setting "static ip" in the interface configuration.

---

### Post by wieman01 on 2006-11-01
> **jpkotta said:**
> I don't know about how to do it in network manager, but you can do it in network-admin.  I keep network settings for home and school separate this way.

Set the settings how you want.  Then go to the top bar of the gui and do an "create location".  Repeat for each location.

You can request a fixed IP address by setting "static ip" in the interface configuration.
That is true. But the GUI cannot cope with WPA, it's WEP only (encryption). WPA is the reason why everybody is relying on NetworkManager or Wifi-Radar.

---

