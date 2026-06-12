---
title: "Staticip problems"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by KuriKai on 2008-04-09
I have a problem
My wireless router crashes if it gives out ip addresses, so I have to give each computer one manually.
This means I can not use wireless roaming on my laptop. because the laptop does not acquire an ip from the router
So I choose manual and set it to static.
I set up everything correctly except for "Password type". There is no option to choose to use "no security key". So I can not use because I choose not to use a "wpa" or "wep" key.

Anyone know how to set it up with a static ip and not needing a security key?

---

### Post by wieman01 on 2008-04-09
Network Manager cannot handle static IP addresses yet. The next version might.

You can revert to command line, however. See this for more:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

Another option would be [WICD]("http://wicd.sourceforge.net/").

---

### Post by KuriKai on 2008-04-12
I followed the static guide
and now I get this in the command line
```

Listening on LPF/wlan0/00:20:ed:79:1c:35
Sending on LPF/wlan0/00:20:ed:79:1c:35
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

