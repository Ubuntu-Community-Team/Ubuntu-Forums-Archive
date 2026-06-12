---
title: "LevelOne WNC-0301 v2 problem"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by joylay83 on 2007-05-12
Hi guys,
I just installed Ubuntu Fiesty 1 day ago after trying the Live CD. Everything is working fine except my wireless card ([WNC-0301]("http://global.level1.com/products2.php?Id=16")) RT2500 chipset.:( 

Things i did:
uninstall network manager : didn't work
Install RuTilt: didn't work
Install R2500 driver from serialmonkey: it says driver is installed already and won't allow me to install
Replace driver with windows driver through ndiswrapper: same as above
Add rt2500 native driver to blacklist and try again: same as above
Disable IPv6: didn't work
connect to wired LAN and update via update manager: same as before

As of now, it recognize my device as ra0. i am able to enter my essid and it can detect a connection, but cannot surf the internet and signal strength is 0. 

my card is not in this list: [Ubuntu Supported Cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Really grateful if anyone can help me... Thanks in advance.

EDIT: update
I assigned a static up via network manager manual configuration and it worked.:D but i want to connect via dynamic ip.

---

