---
title: "T60/Atheros/ath0:avahi/no ip/no connectivity/HELP"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by absolutx on 2008-08-08
Hello,

I'm new to ubuntu and kinda new to linux. I went linux about 6 months ago and I don't even dual boot with windows anymore. I just use Ubuntu (hardy) which is very very cool. Since the "change" I have had issues with my wireless connection, it sometimes worked, sometimes it didn't. I used to configure Network Manager in manual configuration and that was the only way wireless worked, when it was in broadcast mode it didn't. So I started to download a bunch of network related packages from package manager and now I made it kinda useless, it never works... I can still "see" the available wireless networks but can't seem to get a valid ip address from the routers. I say routers because I have tried with a bunch of them... linksys, dlink, netgear... I even have a linksys with ddwrt firmware and have been unable to connect to that one too, so it's probably not a router thing. I'm really not an expert on the wireless thing but I used to have Redhat before Ubuntu and I remember my driver was ath0_pci. My network card is an Atheros no idea which (I'm on a thinkpad T60 if that helps...) and I don't know if doing the madwifi driver install works for me and I'm scared to make my ethernet (that still works fine) go away. Another thing that happened was that I got a new adapter called ath0:avahi and I'm getting one of those generic ips 169.254.etc.. I used to have my eth0, lo, ath0 and wifi0. When I was on wireless the one that worked was ath0 but with the new mysterious ath0:avahi it doesn't work. ath0:avahi is kinda overtaking the ath0, so I no longer get an IP on that adapter. Any ideas on what I can do? (please don't say reinstall ubuntu =). Thanks

---

### Post by NuxIT on 2008-08-22
I know this isn't what you want to hear but I'm in the exact same boat. I used to use WEP with the ath_pci driver just fine in 7.04 and 7.10. Ever since going to 8.04 and trying to get WPA working my wireless doesn't work at all! After spending countless days trying and reading I'm giving up and going to try and reload back to 7.10. Everything about ubuntu is user friendly except wireless configs. Esp WPA.. Man they really need to make this easier! :confused:

---

### Post by Magicked on 2008-09-04
I had problems getting an IP address with madwifi as well.  In ifconfig, I could see ath0 and wifi0 and everything seemed to be fine.  Also, I could scan for access points with the card and it found all the ones I would expect.  We are using WPA on our network, and even though I typed the key in network manager with Ubuntu, I couldn't get it to assign me an IP address with dhclient.  After looking through the Madwifi documentation, I found this:

[http://madwifi.org/wiki/UserDocs/UsersGuide#wpa-EnableDisableWPAWPA2Support](http://madwifi.org/wiki/UserDocs/UsersGuide#wpa-EnableDisableWPAWPA2Support)

This led me to just open a terminal and enter the following:

sudo iwpriv ath0 wpa 3

And BAM! I had an IP address.  Hope this helps someone! :guitar:

---

