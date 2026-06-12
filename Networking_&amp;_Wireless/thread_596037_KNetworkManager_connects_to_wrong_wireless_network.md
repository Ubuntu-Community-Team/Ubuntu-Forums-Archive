---
title: "KNetworkManager connects to wrong wireless network on startup"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by slimdanny on 2007-10-29
Hi,
KNetworkManager on system startup connects to an unsecured neighbours' network instead of mine. when i try to click on my network it shows the progress bar and then connect to the neighbours network again.

Here's what i tried so far, and nothing worked:

1. moving neighbours network to untrusted list of networks in the options

2. switch to offline mode in the options then back to online mode.. after doing that KNetworkManager doesn't see any network, but connects to neighbours' network again.

3. disable wireless in the options then enable wireless again.. KNetworkManager crashes.

ideas? 

Thank you.

---

### Post by slimdanny on 2007-10-30
FIXED!

here's how to fix:

1. close KNetworkManager
```
Right click on the icon in the tray , click quit
```

2. open ~/.kde/share/config/knetworkmanagerrc file, this is where KNetworkManager keeps all networks it ever connected to.
```
kate ~/.kde/share/config/knetworkmanagerrc
```

3. delete network that you don't want to connect to
```

[Network_IGvT0KHSdXiF1Sua]
ESSID=default
Encryption=none
Timestamp=2007,10,28,17,25,49
Trusted=false

```

4. Done!. Reboot.

Hope that helps others

---

