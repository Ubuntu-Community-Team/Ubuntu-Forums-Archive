---
title: "Network Settings resetting itself"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by Ninjagecko on 2005-11-26
Hello.

Might anyone know how to indefinitely set a preferred network ESSID to connect to?

Problem: My new Breezy install is unable to connect to the network at bootup; the Network Settings resets itself back to almost default settings, forcing me to re-enter the name of the network I wish to connect to each and every time I boot up.

Infact, the name of a better network settings manager would be greatly appreciated.*

Thanks for the assistance.

*(the default control panel doesn't have location functionality despite it being present in the GUI, doesn't seem able to list detected networks, and is pretty unintuitive, e.g. the obscure "enable this connection" option making the connection reactivate themselves mysteriously...)

---

### Post by Lambert on 2005-11-26
There are some utilities you can look at that are gui driven.

gtkwifi; wifiradar, or network manager

With out these there is also a way to set these in the /etc/network/interfaces file. 

If you post the current settings in that file someone could tell you what to add to automate start up.

---

