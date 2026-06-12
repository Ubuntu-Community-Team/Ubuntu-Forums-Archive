---
title: "Wireless problems"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Sheneron on 2008-04-26
I am new to ubuntu and just installed the Hardy release.  Everything works fine except for my wireless.  I am using a Gateway MT3705 computer.  Can anyone help me?

---

### Post by Sheneron on 2008-04-26
Ok my wireless is working, but I had to have it not have a password.  I read something that I can't connect to WPA.  Does anyone know anything about this?

---

### Post by wilsonmuse on 2008-04-26
Here's some information: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Basically, if your device or driver doesn't support WPA then Ubuntu can't. Otherwise Network Manager should be able to use it.

Try to connect like this:
1) click on the Network Manager Icon on your Gnome panel.
2) select "Connect to Other Wireless Network...".
3) change "Wireless Security:" to WPA and fill out the rest.

---

### Post by Wharf Rat on 2008-04-26
I just resolved a similar issue.

Upgraded to 8.04 and no wireless connection on a Lenovo T61.  I could see the wireless hot spot but not connection.  It kept saying "Waiting for Key from network."

I use WPA/2 on a home net.  

1. I disabled my WPA security on the router, laptop then had to remove (edit) wireless networks.  Once I established contact, it would work without security.

2.  I am using the Atheros propriety drivers.  I disabled them and rebooted.  Once up, no network at all.  Re-engaged the drivers and my laptop latched onto the network then asked for a password.  All seems to be working now.  ???

---

### Post by Sheneron on 2008-04-26
Thanks that worked for me

---

