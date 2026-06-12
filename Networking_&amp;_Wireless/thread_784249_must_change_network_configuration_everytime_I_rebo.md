---
title: "must change network configuration everytime I reboot"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by ThePiper(Pied) on 2008-05-06
Hullo,

I have a somewhat strange problem.  
Every time I restart my computer, linux won't establish an internet connection until I go into network manager and reconfigure my netwrok connection by retyping my passkey and changing the protocol from WPA to WPA2.  After I do that everything works fine, but I am wondering why it doesn't remember the correct settings upon reboot.  I checked in my /etc/network/interfaces file and everything in there looks correct, and nothing changes after I reconfigure using network manager.

Here is what it says with the psk and ESSID taken out both before and after network reconfiguration using Network Manager:

iface eth1 inet dhcp
wpa-psk <hex-key>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid <ESSID>

However, when I check ifconfig/iwconfig before and after reconfiguring there are changes that have occured, which makes sense because now I have an active internet connection.  

It doesn't appear to be a wireless issue either because I cannot connect hardwired until after I reconfigure either.

Any insight would be appreciated.

-Josh

---

