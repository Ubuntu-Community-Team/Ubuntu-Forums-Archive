---
title: "TPLink TL-WDN4800 (Atheros AR93xx) will not connect to wireless"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by ashughes on 2015-01-19
I am unable to get my new wireless card (PCIe) to connect to my wireless network. I'm just in the Ubuntu 14.10 installer and cannot get connected to the internet to install updates. I've tried several troubleshooting tips I've found around the internet, including loading and unloading the ath9k module. Every time I try to connect to my network it times out.

dmesg reports:
```

wlan0: authenticate with *macaddress*
wlan0: send auth to *macaddress* (try 1/3)
wlan0: authenticated
wlan0: aborting authentication with *macaddress* by local choice (Reason: 3=DEAUTH_LEAVING)

```

Does anyone have an idea how I might resolve this? I've been researching this for several hours and nothing I've found so far has resolved the issue.

---

### Post by ashughes on 2015-01-19
Nevermind, I just proceeded with the installation sans internet and my wireless connected after rebooting into my new install. I'm not sure why it wouldn't work in the installer but I probably should have tried that before posting this thread and tearing my hair out. It just means I have more work to do post-installation re: 3rd party software and updates.

---

