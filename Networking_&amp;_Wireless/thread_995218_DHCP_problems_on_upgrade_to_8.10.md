---
title: "DHCP problems on upgrade to 8.10"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by thunderbunny on 2008-11-27
I just upgraded to 8.10 and (as always seems to happen) I have a new array of problems connecting to wireless networks. I'm using Madwifi and rebuilt it for the new kernel. I can scan for networks okay, but can't get an IP address from my network (unencrypted). When I 'sudo dhclient wlan0', I just get a series of "DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4" followed by "No DHCPOFFERS received". Any suggestions? What did everybody else have to do with dhcpclient.conf after upgrading?

---

### Post by thunderbunny on 2008-11-27
...guess nobody has any insight. I'll keep looking on Google.

---

### Post by thunderbunny on 2008-11-27
Okay, so I built MadWifi off of a snapshot (dated 11/05) and also installed dhcpcd (which I don't know if that has anything to do with it) and now it's working. Go figure.

---

### Post by thunderbunny on 2008-11-27
...and it's broken again. It worked for about 10 minutes, stopped, and now I can't reconnect.

---

### Post by thunderbunny on 2008-11-28
My wired interface connects okay, leading me to believe that this is a driver issue, not a DHCP issue. I'm now using the ath5k that I built myself from the source as of 11/26.

---

