---
title: "Wireless Not Working After Return From Suspend"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by cas0586 on 2014-01-02
Fr personal preference I would like to configure my wireless connection upon boot. This way wireless is connected when desktop loads and weather, etc is loaded. Anyways, I edited **/etc/network/interfaces **as such:

```
 # interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


auto mlan0
iface mlan0 inet dhcp
wireless-essid WIRELESS
wireless-key **********

```

So, perfect everything is loaded on boot correctly. I am now left with network-manager-gnome indicator icon in the gnome panel(using gnome-classic on 12.04) that not do anything. So, I removed the package:

```
sudo apt-get remove network-manager-gnome

```

Reboot and network manager connection indicator in panel is now gone. I thought everything was fine until brought back from suspend and the connection did not reconnect automatically as it did with network-manager-gnome managing the connection.

So my question is how can I retain my current setup but have it reconnected when returning from suspend? TIA!

---

### Post by cas0586 on 2014-01-02
Alright. Did a bit of research and solved the issue! Found the answer here:

[http://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410](http://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410)

---

### Post by chili555 on 2014-01-02
Is your driver iwlwifi or did you substitute the actual mlan0 driver?

Your settings imply WEP encryption; I recommend you upgrade to WPA2-AES.

---

### Post by cas0586 on 2014-01-04
> **chili555 said:**
> Is your driver iwlwifi or did you substitute the actual mlan0 driver?

Substituted iwlwifi with the mlan0 driver after identifying it.

 ```
cas@Series3:~$ sudo lsmod
[sudo] password for cas: 
Module                  Size  Used by
nls_iso8859_1           3126  1 
nls_cp437               4658  1 
vfat                    8958  1 
fat                    45523  1 vfat
fuse                   63518  2 
rfcomm                 21680  12 
uvcvideo               59825  0 
videobuf2_vmalloc       2772  1 uvcvideo
isl29018                6972  0 
industrialio           14616  1 isl29018
sbs_battery             6776  0 
joydev                  8513  0 
mwifiex_sdio           13826  0 
mwifiex               106470  1 mwifiex_sdio
cfg80211              164044  1 mwifiex
btmrvl_sdio             8324  0 
btmrvl                 11905  1 btmrvl_sdio
bluetooth             192270  22 rfcomm,btmrvl_sdio,btmrvl
rtc_s3c                 6827  0
```

```
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]sudo nano /etc/pm/config.d/config[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR][/LEFT]
```
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]SUSPEND_MODULES=cfg80211[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#000000][FONT=Ubuntu Mono]

Did the trick for me![/FONT][/COLOR][/LEFT]

---

