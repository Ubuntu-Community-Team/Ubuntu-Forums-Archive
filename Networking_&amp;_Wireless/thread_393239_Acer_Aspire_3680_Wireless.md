---
title: "Acer Aspire 3680 Wireless"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by djotaku on 2007-03-25
Hey there!

First time Ubuntu user (been using Fedora for about 4 years) and I installed it on a laptop.

I'm trying to get wireless to work.  I think I may be missing just one step.

I read ([http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)) because my wireless network has WPA.  However, this seems to require hardcoding the information and I would like the wireless to work with different networks - so I don't think I want to hardcode it.

As a semi-veteran of linux, here is all the info I think you may need.

-ran lspci
0a:03.0  Ethernet controller:  Atheros Communications, Inc.  AR5005G 802.11abg NIC (rev 01)

-If I run iwlist scan, it finds my network and says Encryption key: on

-if I run iwconfig it's ath0 that looks like the one that would connect except that Access Point:  Not-Associated and wifi0 says no wireless extensions

-under the NetworkManager Applet 0.6.3 - it only lists wired network - not the wireless one

-System -> Administration -> Networking it shows Wireless connection and it has a check mark.

Thank you!  and let me know if you need more info!

---

### Post by Hase on 2007-03-25
I just installed Edgy on a new Aspire 3680 and wrote [this]("http://www.ubuntuforums.org/showthread.php?t=392666") to help others.  The first section describes my settings for wireless.  I don't use network-manager because I find it to be annoying, I prefer setting up the protected networks as entries with priority rankings and just letting the system automatically connect to the appropriate network depending upon where I am.  Post here or there if you have any questions about my setup.

---

### Post by handaxe on 2007-03-25
check that you have wpa_supplicant installed. Should be there as a dependency of NetworkManager.

In don't run NM, but I recall that /etc/networking/interfaces needs to have the interfaces commented out that you wish NM to manage. Search the forums for details on this if you need.

An alternative to NM is Wicd (and there is Wifi-radar as well).

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by entering /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper) as a startup proggie (I am a long term Gnomer - its system -> preferences -> sessions; KDE is a mystery to me...)

See how this goes. Good on different encryption types, and makes WPA partic easy You might uninstall any other managers first.

HA

---

### Post by djotaku on 2007-03-25
Your tutorial there fixed my speaker issues!

And the wireless now works!  Thanks a bunch!

---

### Post by Hase on 2007-03-26
You're very welcome! :p

---

