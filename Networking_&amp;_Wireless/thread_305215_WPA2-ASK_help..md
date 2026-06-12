---
title: "WPA2-ASK help."
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by winter_mute on 2006-11-23
I left for college, and my dad bought a new router.  He wants to use the most secure setting on it - I believe it's WPA2-ASK according to him, and I can't connect to it with Edgy.  I can detect it, I can connect to it in WEP mode, but I can't connect in WPA2-ASK or TKE or something along those lines.  He's not sure.  I'm running a Dell e1505 with Intel Pro/Set wireless.  Is there some way that I can set up a good wireless network manager (preferably something better than what comes installed default in Edgy) and get WPA2 security?

---

### Post by wieman01 on 2006-12-24
Is that still a problem?

---

### Post by SugarDaddy on 2006-12-24
The most secure setting is WPA2 (q.v. WPA) where WPA-PSK refers to the fact that you have a single Pre-Share Key (a la password) that everyone uses versus individual keys for each user. WPA2 combined with hidden SSID (broadcast disabled) and MAC Address Filtering is the most secure wireless setting currently. Assuming that your router is configured such:

First, you need to install wpa_supplicant. luca_linux's post [HowTo: WPA with wpa_supplicant]("http://www.ubuntuforums.org/showthread.php?t=263136") is a good thread for walking you through how to install wpa_supplicant and getting familiar with the wpa_supplicant.conf file and the /etc/network/interfaces file. Follow this step by step guide then return here for the correct settings of the wpa_supplicant.conf file for WPA2 and hidden SSID.

[URL="http://www.ubuntuforums.org/showthread.php?t=263136"]http://www.ubuntuforums.org/showthread.php?t=263136
[/URL]
Second, you need to make sure the wpa_supplicant.conf is set up properly for hidden SSID and WPA2. To edit type the following command in a terminal:

```
sudo gedit /etc/wpa_supplicant.conf

```This will bring up the wpa_supplicant.conf file and it should be edited to look something like this:

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
    ssid="your SSID here in quotes if ASCII"
    scan_ssid=1
    proto=RSN
    key_mgmt=WPA-PSK
    group=TKIP
    pairwise=TKIP
    psk="your password here in quotes if ASCII"
}

```The important variables are AP_SCAN=2 which enables the wireless card to scan hidden SSID. PROTO=RSN sets the encryption mode to WPA2. Many other posts often have WPA and RSN in the variable list for PROTO. When AP_SCAN=2 the security settings cannot be general but must be specific (i.e. only one variable in the list). The same goes for KEY_MGMT, GROUP, and PAIRWISE. Most linksys routers use TKIP versus CCMP. So if you have for example "group=CCMP TKIP" delete CCMP from the list.

Once the changes are made to wpa_supplicant.conf, save the file then reboot the machine. You should be online!

---

