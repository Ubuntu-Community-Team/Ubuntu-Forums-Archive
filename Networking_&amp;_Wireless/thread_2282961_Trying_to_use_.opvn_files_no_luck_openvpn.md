---
title: "Trying to use .opvn files no luck openvpn"
date: 2015-06-18
forum: Networking &amp; Wireless
---

### Post by nufc179 on 2015-06-18
[SIZE=2]hi i new to ubuntu i have a VPN provider and i have got all the .opvn files with the info on the keys (ect) but when running[/SIZE] [SIZE=3][COLOR=#ff0000][/COLOR][COLOR=#ff0000]sudo openvpn --config "SwitchVPN - EU - France.ovpn[/COLOR][/SIZE][COLOR=#ff0000]"[/COLOR][COLOR=#000000] 
all i get is [/COLOR]Options error: In [CMD-LINE]:1: Error opening configuration file: SwitchVPN - EU - France.ovpn
Use --help for more information.
[COLOR=#006400][SIZE=3]help its got my life[/SIZE][/COLOR]

[COLOR=#006400][/COLOR]ps have ran as ROOT same thing

---

### Post by crip720 on 2015-06-18
I have the same problem as you do, but with Nordvpn.  You might be able to use Network manager if you create an openvpn and import the config files with network manager.  I find that I can use the command line to connect if I start right from the beginning by redownloading the config files unzipping them and then connecting to the vpn.  It only works once.  See the Linux tutorials at nordvpn.com for full instructions for network manager and terminal.  I hope that someone else on the forums can help us out.   Colin.

---

