---
title: "Can Network Manager perform 'ap_scan=2' to reconnect to hidden AP?"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by Corvo78 on 2007-02-06
I'm using Ubuntu 6.10 for 2 weeks now (and Linux in general) and I'm progressing quite nicely with my install.
I've disabled my auto-login, installed ndiswrapper, installed Gnome's Network-Manager and installed PAM-keyring.

So, as long as an Accesspoint (AP) broadcasts the SSID everything works perfectly.
*...however, and one might have guessed it: my AP's SSID is hidden.*

As far as I can gather, the Network-manager should be able to reconnect to a hidden AP once it has been able to store the 'bssid' (anyways, some reverse method of re-identifying a hidden AP).
If one uses wpa_supplicant only (no network-manager gui) the solution should be to include 'ap_scan=2' in the 'wpa_supplicant.conf' file.


Problem is: In order for network-manager to work, the '/etc/default/wpasupplicant' file was created containg the line 'ENABLED=0', preventing me to configure the 'ap_scan=2'.
**In what way (file) can I configure Gnome's Network-manager to scan for hidden SSID's (aka ap_scan=2) ??**

I'm trying to make all this work on my DELL Inspiron 8600c laptop using WPA-PSK/TKIP.


I'm so close, yet so far ;)
On a sidenote: Beryl makes vista look feeble :D

---

### Post by spd106 on 2007-02-06
You access Network Manager settings in gconf-editor, under the system/networking/wireless/networks. When you first connect to a network it will store the settings and you should be able to autoconnect next time the essid appears.

Sadly this doesn't always work, I think that the best way to get this working is to stick with wpa_supplicant directly. Though you could always build NM 0.7 from cvs, see [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

---

### Post by Corvo78 on 2007-02-06
Thanks for the hint.
*goes googling for a wiki on gconf editor* --> *[http://en.wikipedia.org/wiki/Gconf-editor](http://en.wikipedia.org/wiki/Gconf-editor)*

Very interesting and hopefully this works, will report back (soon)!

---

### Post by Corvo78 on 2007-02-08
My conclusions thus far:[list][*]When in Windows-XP a wireless site survey shows my hidden AP with no name and only it's BSSID (it's MAC address?).
[*]Using gconf-editor in Ubuntu reveals that network-manager has properly stored all information regarding my hidden AP.
[*]Reading the /var/logs/daemon.log reveals that in general gnome's Network-manager uses "AP_SCAN 1"
[*]"AP_SCAN 2" is only used if I specifiy 'connect to other wireless network'.[/list]


So, in theory it should be possible. But for the time being I don't seem to be able to let gnome's Network-manager use "AP_SCAN 2" all the time.

---

