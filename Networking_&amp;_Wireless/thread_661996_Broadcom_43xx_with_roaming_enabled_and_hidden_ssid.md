---
title: "Broadcom 43xx with roaming enabled and hidden ssid"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by mr bob on 2008-01-08
Thought this may help some people:

I have 7.10 Gutsy installed and have a Broadcom 43xx wireless card with a network with WPA2 security, roaming enabled and a hidden ssid.

Before the network was hidden I prefered ndiswrapper but once I hid the network, ndiswrapper could not connect as it could not see my network. Installing wcid didn't help.

However, I found that returning to the bcm43xx driver (in the restricted driver manager in 7.10) with the standard NetworkManager I can connect to a hidden ssid and it keeps the details if I reboot or suspend/resume.

The only bug was on resuming from hibernation (s2disk - in my case). The network appeared to be connected but wasn't. If I clicked on the NetworkManager icon and select my network twice it reconnected but I wanted to do it automatically and I have found a way:

I edited the following script:
```

sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

```

and put at the bottom just before the exit command:
```

iwconfig eth1 essid <insert the name of your network here>

```

I'm sure this isn't the best script to put the command in but it works for me. Whether it works for other people probably depends on the type of hibernation they are using.

But if you are using the bcm43xx driver and are having trouble with wireless network on resuming from hibernation then it would be worth trying the above command (preceded by sudo) in a terminal to see if it fixes the bug.

---

