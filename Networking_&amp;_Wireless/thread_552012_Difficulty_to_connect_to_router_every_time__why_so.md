---
title: "Difficulty to connect to router every time / why so random?"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by jchgf on 2007-09-15
I am wondering why sometimes I can connect to my router, and why sometimes I can't.

Right now it is working nicely. I had to restart my machine and I was logged in directly from the get-go without having anything to do. 

Most of the time though, the wireless network icon shows that my router has been found and is sending and receiving packets, but the process of connecting to the router apparently never finishes, as if it was awaiting some sort of authorization. 

The router is encrypted in WPA.

I have the latest versions of Network Manager Gnome, WPA Supplicant under Ubuntu 6.06.

It seems like there are so many variables that could affect this, but it also seems quite random. I don't know any modifications that happened to my laptop or my router before I was unable to connect. Now it works like magic.

I understand my question is vague, but any tips that could help me determine why my connection to the router is so seemingly random and what steps I should take when the access is difficult would be appreciated.

---

### Post by spd106 on 2007-09-18
There should be error messages logged in the /var/log/syslog file. That might point to where the problem is coming from.

What kind of card/driver do you have?

Have you tried starting network manager in debug mode, there's instructions on this [FAQ]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ") and more information [help docs]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") page

---

