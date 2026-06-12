---
title: "ndiswrapper network &quot;hiccups&quot;"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by Absurd on 2008-02-08
So, I got my usb wlan NIC working with ndiswrapper (with WPA in networkmanager), but I have one annoying problem. It seems that, after a few minutes, I have to tell networkmanager to reconnect me to the network. The connection is just dropped.

Is there a way around this?

Should I remove /etc/modprobe.d/ndiswrapper?

---

### Post by tangibleorange on 2008-02-08
I don't think removing the file will solve anything. A lot of people have problems with Network Manager. You could try uninstalling it with Synaptic and trying [WICD network manager.]("http://wicd.sourceforge.net/") It certainly worked for me.

---

### Post by Absurd on 2008-02-08
> **tangibleorange said:**
> I don't think removing the file will solve anything. A lot of people have problems with Network Manager. You could try uninstalling it with Synaptic and trying [WICD network manager.]("http://wicd.sourceforge.net/") It certainly worked for me.

well, I've been trying like hell to get my wlan working, so I'd be nervous about using something else

does WICD run as a daemon?

[edit]just tried WICD and it didn't work

---

### Post by tangibleorange on 2008-02-09
OK. Do you know what network card you have and it's chipset?

---

### Post by Absurd on 2008-02-09
Yes, and there are open source drivers available, but I couldn't get them to work (with wpa). (rt2870)

[update]I got around this problem by setting my router's wireless mode to G only. Is "G only" backward compatible or would I have to get an adapter with wireless G supported to connect another pc to it?
[edit]spoke too soon :(

---

