---
title: "Repeater and main router conflict"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by login-0z on 2014-02-02
Hi,

I have a wireless ADSL router and a second router configured as a repeater. Usually, the final result is that the PC is only seeing one SSID and connects to the most appropriate one (probably the one with the strongest signal). For me, this works exactly as expected on Mac and Windows platform, but I am stuck with Ubuntu: I always see my network twice (the original router with low signal and the repeater with high signal). As it only rely on SSID, I cannot see, in ubuntu menu, which is which device (they appear as "my_ssid 1" and "my_ssid 2" in the menu. But selecting one or the other is the same result...) I only know that I am connected to the wrong one because of the low and unreliable signal. I also confirmed using "Wii radar" that I am connected to the wrong one with the weakest signal.

My question is the following: Is there any way to force Ubuntu to always take the strongest signal without manual operation ?

If not, is there a way to force ubuntu (which is usually always in the same room) to connect to a specific device (using for example the HW address) ?

Please note that I already tried "iwconfig wlan0 ad aa:bb:cc:dd:ee:ff" to force to connect specifically to the repeater. It basically seemed to work based on the signal strength, but I then have no connection at all to internet or any other machine in the network... this is probably not the good solution.

As my children are using the linux machine, I would appreciate any solution that doesn't require to type "sudo..." :-)

Thank you for any help.

Ubuntu 13.10
Wireless 802.11n, WPA secured.

---

### Post by steeldriver on 2014-02-02
It should be possible by setting the connection BSSID equal to the MAC address of the access point you want to lock to

[ATTACH=CONFIG]250023[/ATTACH]

You can list the visible BSSIDs using nm-tool or

```

nmcli dev wifi list

```

---

### Post by login-0z on 2014-02-08
Hi,

Thanks steeldriver... it was too easy: everything was already designed in the graphical interface... I was looking too far :-).

Best regards.

---

