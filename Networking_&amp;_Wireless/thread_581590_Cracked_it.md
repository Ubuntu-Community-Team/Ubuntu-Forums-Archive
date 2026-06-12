---
title: "Cracked it"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Pete051 on 2007-10-19
Upgraded to gutsy last night and promptly lost my wireless connection after trying all day to get it back I found the solution. use the old 2.6.20-16-generic kernel and the rt61 module not the rt61pci.
I did find I had to install the nvidia kernel to get more than 800 x600 resolution though. but otherwise gutsy looks good :)
PS I used this thread  [http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)

---

### Post by Agent86 on 2007-10-19
> **Pete051 said:**
> Upgraded to gutsy last night and promptly lost my wireless connection after trying all day to get it back I found the solution. use the old 2.6.20-16-generic kernel and the rt61 module not the rt61pci.
I did find I had to install the nvidia kernel to get more than 800 x600 resolution though. but otherwise gutsy looks good :)
PS I used this thread  [http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)Same thing here, I  had RT61 working with WPA in Xubuntu Feisty using the instructions in that thread. Upgrading to Gutsy removed the ra0 interface, added wlan0 and wmaster0 interfaces, and broke the wireless. I just booted back to the 2.6.20-16 kernel, restored my old /etc/network/interfaces file from the backup I made before the Gutsy upgrade, did a ```
sudo /etc/init.d/networking restart
```and I had my RT61/WPA working again.

The strange thing is that I told the Gutsy upgrade (I used the alternate CD method) to delete the 2.6.20-16 kernel. I guess I'm glad it didnt do it :)

I still want to get the RT61/WPA working with the new kernel, so I'll try some things and report back here if I have success.

---

### Post by Agent86 on 2007-10-22
I did get RT61/WPA working in the new kernel. I compiled the legacy rt61 driver by following the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

I had to configure the ESSID and WPA keys by editing the /etc/Wireless/RT61STA/rt61sta.dat file, even though Feisty worked with the out-of-the-box driver and editing /etc/network/interfaces

---

### Post by Pete051 on 2007-10-22
I know of that route to fix the wifi it just seemed to me that the aggravation of compiling the driver out weighed any advantage that the later kernel might have, or maybe I'm just lazy :)

---

### Post by Agent86 on 2007-10-27
I was emboldened by my success in getting RT2500 and WPA working in Ubuntu 7.10 Gutsy after reading this thread:
[http://ubuntuforums.org/showthread.php?t=587727](http://ubuntuforums.org/showthread.php?t=587727)

So I decided to give it a shot with the RT61 in my Xubuntu machine. So I reinstalled network-manager and network-manager-gnome, blacklisted the compiled driver, and removed the ra0 alias to get back to the just-installed state. Then I edited **/etc/network/interfaces** and rebooted. And it worked! I still get errors when I do **sudo /etc/init.d/networking restart**, but in the end it works and I can get on the 'net.

So now I have RT61 and WPA working with the Gutsy out-of-the-box driver (rt61pci) and kernel just by editing the **/etc/network/interfaces** file. This is what my **/etc/network/interfaces** file looks like now:```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
pre-up ifconfig wlan0 down

wpa-psk KeyAfterRunning_wpa_passphrase_AndWithoutQuotes
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MyESSID_WithoutQuotes
pre-up sleep 20
pre-up ifconfig wlan0 up

auto wlan0
```

---

### Post by dburnett77 on 2007-10-29
Winding POST---Mods need to DEL.

---

