---
title: "CCMP: decrypt failed -- Why do I keep getting this message in the system log???"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-05-04
Currently using Kubuntu Feisty with Linksys WPC54GS card - Broadcom chipset (rev 03).  Drivers were installed via use fwcutter. 

Thank you for the excellent guide on how to setup WPA-2 with static IP : [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

The problem I am having however is that after making modifications to the /etc/network/interfaces file my system log is being flooded with this message (small snippet):

[114165.692000] CCMP: decrypt failed: STA=00:19:5b:60:23:07
[114166.196000] CCMP: decrypt failed: STA=00:19:5b:60:23:07

The card works great and I dont get any dropped connections, just wondering why this message is displayed, and in the least would like to supress this error message.  Here is my /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146 192.168.1.1
wpa-driver wext
wpa-ssid GoHilton.com
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <key>

Thanks for any help!

---

