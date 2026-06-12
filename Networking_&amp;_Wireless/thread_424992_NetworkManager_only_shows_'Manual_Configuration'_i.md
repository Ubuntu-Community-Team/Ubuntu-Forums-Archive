---
title: "NetworkManager only shows 'Manual Configuration' in Feisty"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by kvossen on 2007-04-27
The network manager applet in the gnome system tray only display a 'manual configuration' menu item when I click on it. It used to also display my wired and wireless connections, but not since I installed some updates. Anybody experiencing the same problem?

---

### Post by palmerthegeek on 2007-04-27
Kvossen,

I have, I enabled the roaming feature on the wireless confirguration and the applet came back.

Good luck,

---

### Post by kvossen on 2007-04-27
Thank you, that fixed it.

---

### Post by juraj on 2007-06-04
But that way we can't set up a static IP address. What now?

(and I would really like to use the VPN feature in network manager with a static IP address)

---

### Post by vanadium on 2007-06-04
You still have the option "Manual configuration" when clicking the network icon. In Manual configuration, as in previous Ubuntu versions, you can save "locations" with different specific configurations and apply specific settings at any time. Thus, with roaming on, you just have additional features, such as auto-configuring wired networks and discovering and connecting to wireless networks

---

### Post by jeremija on 2007-06-04
I have a similar problem.
I recently installed ubuntu and i have both wireless and ethernet card. I only see manual configuration menu item, whether or not I have romaing on.
In the wireless connection window (System>Preferences>Network>Wireless Connection), on the password select dropdown menu I only see WEP key (hex or ascii) and no WPA keys, but I have wpasupplicant installed. 
I found this page [http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html](http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html) and i realized that i don't have those windows from screenshots.
I also checked the Device manager and saw that my Wireless interface (Intel PRO/Wireless 3945ABG) is known to the system as eth1, not wlan?
I have ubuntu 7.04 64-bit version.


also here is what i get when i type iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:424   Missed beacon:0
```


edit: i managed to make wlan connection work by following this howto: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
but i still don't understand why don't have wpa on my password type dropdown list...

---

