---
title: "WiFi connecting and dropping immediately (ubuntu 16.04, tkip network)"
date: 2017-10-05
forum: Networking &amp; Wireless
---

### Post by Powercat on 2017-10-05
Hey guys,

I've been dealing with this issue at work, can't connect to the Wifi network here.

It works on another of my laptop with the same OS and a different network card, but this Thinkpad T401s with a rtl8191sevb card can't stay connected.

The wifi will connect, ping or any other network service won't work, and after a few seconds it disconnects me. Then it just loops over that endlessly.

Following is the syslog when this happens.

We can see that I'm getting a DHCP lease, but then we start seeing something like "Michael MIC failure detected", and "TKIP countermeasures started" just before "deauthenticating from 02:18:4a:bb:32:f0 by local choice (Reason: 14=MIC_FAILURE)"

The network here is using WPA2 with TKIP (not AES)

Things I tried so far:

Uninstall TLP, disable power saving in the BIOS, disabled wifi card power saving.

sudo iwconfig wlan0 power off

sudo killall wpa_supplicant

Adding "options iwlwifi 11n_disable=1" to iwlwifi.conf

Unfortunately this is not my AP so I have to live with TKIP. Any ideas?

Here is the paste from wireless-info: [https://pastebin.com/M4VtvDqM](https://pastebin.com/M4VtvDqM)

Here are the system logs when this issue is occurring: [https://pastebin.com/zL9NrY0q](https://pastebin.com/zL9NrY0q)

Quite frustrating that this works on 3 out of my 4 machines. Just this one thinkpad 410s is giving me troubles!

Thanks!

---

### Post by Powercat on 2017-10-10
Anyone has an idea?

---

### Post by Powercat on 2017-10-12
Hey everyone, I was able to permanently resolve this issue by installing windows 10. Now the wireless works perfectly!!

---

