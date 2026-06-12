---
title: "Wireless network without a name"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by Monsuco on 2006-10-16
I am considering buying a laptop, but I have one question about WiFi. My school does the wierdest thing with WiFi. They have a standard unencrypted WiFi network, but it doesn't broadcast it's network name. On Windows,if you type in the network name SCRAP wireless in the network settings, it will become able to find the network and connect to it. Can Linux deal with a "nameless network" such as this?

---

### Post by newlinux on 2006-10-16
Yes it can, pretty much in the same way.

---

### Post by newlinux on 2006-10-16
To add, I've done this a few times with my laptop. I use nm-applet, and type in the name of the network I want to connect to (sometimes even networks that are being broadcast aren't always recognized by scanning, but if I know it exists, I type in the name). I hope your school realizes it isn't increasing security (or limiting users who connect) very much by not broadcasting the SSID. Plenty of tools out there to sniff the name out.

---

