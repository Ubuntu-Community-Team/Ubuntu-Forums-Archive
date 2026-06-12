---
title: "DLink DWA-110 stops working in KDE, works fine in GNOME and XFCE"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by Sonadow on 2008-11-29
i realized my previous post had way too little information for people, so i decided to 'close' it and start new with amore information about the problem.

I managed to get my system to detect my wireless using NDISwrapper and NDISgtk. But i was not satisfied with a GUI frontend: a GUI frontend can break anytime when you least expect it, so i tried from the command line.

I installed Ndiswrapper 1.9 from Synaptic, including ndiswrappers-utils 1.9 and ndiswrapper-common. (leaving out NDISgtk this time)

then i did the following:

```
cd Desktop
```

because i had the drivers on the desktop for easier management, followed by

```
 sudo ndiswrapper -i <drivername>.ini
ndiswrapper -l
sudo modprobe ndiswrapper
```

GNOME, KDE and XFCE worked up to this point, where the device fired up and started to 'see' wireless networks.

From here, GNOME and XFCE just ran away with it by themselves: i just selected the network, keyed in the WEp and i was up.

in KDE, after selecting the network, KDE did not manage to connect, even after repeated prompts for my WEP key. I went into manual config, chinged the system to dhcp, entered in my ESSID and WEP key as hex and hit 'ok', but the system just refused to accept the change: 'dhcp' was immediately unselected, the ESSID and WEP key remained black, and Hex was changed back to ACSI.

I tried to run
```
sudo iwconfig wlan0 ESSID <name of network>
sudo iwconfig wlan0 Managed
sudo iwconfig wlan0 key RESTRICTED <key>

(the codes may be wrong because im currently remembering them off the top of my head now that im back in GNOME)


```

but with little effect. Lastly,

```

sudo dhclient wlan0
```

only threw up a lost package that failed to ping.

Someone help me out please? Any assistance will be most appreciated.

EDIT: This is not the first time i had problems with KDE: it was the same story with Fedora Core some 4 years ago.

---

