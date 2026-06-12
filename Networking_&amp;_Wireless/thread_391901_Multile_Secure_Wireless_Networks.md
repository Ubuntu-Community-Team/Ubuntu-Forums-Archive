---
title: "Multile Secure Wireless Networks"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by HolyIbanez on 2007-03-23
I'm new to Ubuntu, and to linux on a laptop, and am giving wireless a good run.

I am running Ubuntu 6.10.

What I have thus far:

1)  ndiswrapper-utils-1.8
2)  My BCM drivers.
3)  ndiswrapper in /etc/modules (since I had to modprobe it in the Ubuntu dock, I figured it should be loaded automatically, though I might write a script to run my wireless, which will start with a modprobe, and then would remove it from this file).
4)  WIRELESS WORKS!

I felt pretty accomplished having done all that in about 15-20 minutes.

Then I realized the networking tool didn't have an option for multiple WEP networks, and only supports WEP.

Since I don't have to worry about WPA (yet) on the networks I frequent, I haven't bothered configuring wpa_supplicant.

I see my network info in /etc/networking/interfaces.

I have to admit the file makes some sense (I come from gentoo, and my network setups there are stored in /etc/conf.d/net, and look way different), but I can't seem to find a way to add multiple networks.

So, time for my questions:

1)  Does wpa_supplicant support a list of WEP and WPA networks and support on the fly 'hotspot' connections?
2)  Is there a way to store multiple networks in /etc/network/interfaces for the same device?
3)  Is there a way in WPA Supplicant to store unsecure networks with non-broadcast SSIDs?

Thanks!

---

### Post by dbott67 on 2007-03-23
network-manager is a great package for managing wifi (WEP64, WEP128, WPA1 & WPA2).

```
sudo apt-get install network-manager-gnome
```[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]
More details here:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

-Dave

---

### Post by HolyIbanez on 2007-03-23
Well, it took me awhile to even get this working.

And it does work... sorta.

I need to debug why when it resumes from suspend it doesnt quite act right.

What really is annoying me is once I connect to my network (WEP, non-bc SSID), it works, but if I reboot, it forgets about my network, which is really annoying.

Any ideas?

---

### Post by HolyIbanez on 2007-03-24
bump...

---

### Post by dbott67 on 2007-03-24
I'm not sure if it's because your AP is not broadcasting the SSID.  My laptop connects automatically to my own (D-Link DI-614+, 128-bit ASCII WEP, Broadcasting SSID).  network-manager also picks up a few of my neighbours' APs.

As a test, try setting the AP to broadcast the SSID to see if it picks it up automatically.

If you don't want to broadcast the SSID, you'll probably have to connect manually each time:
1. Left-click the nm applet in the gnome panel
2. Select **Connect to Other Wireless Network...**
3. Enter your network info

Or you'll have to write a shell script that configures your wireless.  For example, assume your wireless NIC is **wlan0** and your SSID is **holyibanez **and your using a 128-bit WEP ASCII key **ascii-wep-key:**
```

#!/bin/bash
sudo iwconfig [COLOR=Blue]wlan0[/COLOR] essid "holyibanez" key s:[COLOR=Blue]ascii-wep-key[/COLOR]
```

There are more options & settings.  Try **man iwconfig** for more info.

Hope this helps.

-Dave

---

### Post by domzo on 2007-03-24
I posted a python script the other day that I find useful for connecting to multiple wireless hotspots:

[http://www.ubuntuforums.org/showthread.php?t=390697]("http://www.ubuntuforums.org/showthread.php?t=390697")

Might help?

---

