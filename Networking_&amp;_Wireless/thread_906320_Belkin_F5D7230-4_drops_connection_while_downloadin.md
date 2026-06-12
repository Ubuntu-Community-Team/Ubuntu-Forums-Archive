---
title: "Belkin F5D7230-4 drops connection while downloading in Ubuntu"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by rakusson on 2008-08-31
hi,

I am using Hardy Heron and connect to the Internet through Belkin wireless router F5D7230-4. I have experienced a problem recently. When I try to download something from ubuntu, surprisingly, the network connection drops and I can no longer use Internet! 

Another surprising thing is that my Router's "DHCP client list" doesn't shows my computer!!! (I have attached screen shot, my computer name is Ramesh-T40 and is not in the list but I am still connected and using Internet, even when posting this message!!!). What could be the problem? Though the connection drops periodically in WinXP as well but never on downloading and I can see my computer name in the list.

What could be the problem and possible solution?

---

### Post by jaakan on 2008-08-31
1. DHCP client list is not a static list ( only shows what currently connected )
2. since it drops on both Windows and Linux you need to check all the settings of your router.

if you have wireless Channel set to AUTO you need to change it to say IE: 5, 6 or 7 of like 1 to 11. AUTO means anytime there are too many other router on the same channel your router will jump to another channel and drop all it's wireless connections

Make sure you use MAC level filtering, PC-name xx-xx-xx-xx-xx-xx-xx

or you just could have a bad router. I had a .11b router that would lock up if there was a lot of traffic. if would reboot but the wireless part of it 50% of time didn't start back up without another reboot.

---

### Post by rakusson on 2008-08-31
> **jaakan said:**
> 1. DHCP client list is not a static list ( only shows what currently connected )
2. since it drops on both Windows and Linux you need to check all the settings of your router.

if you have wireless Channel set to AUTO you need to change it to say IE: 5, 6 or 7 of like 1 to 11. AUTO means anytime there are too many other router on the same channel your router will jump to another channel and drop all it's wireless connections

Make sure you use MAC level filtering, PC-name xx-xx-xx-xx-xx-xx-xx

or you just could have a bad router. I had a .11b router that would lock up if there was a lot of traffic. if would reboot but the wireless part of it 50% of time didn't start back up without another reboot.

Yes, I took that screenshot (the posted) when I was still connected to the router. When I do the same thing in the Windows, my computer shows up in the list but not on Ubuntu even when I am connected.

I connect to the channel 11. I am using a Belkin F5D7230-4 G wireless router. There is a persisting problem regarding connection drop even in Windows, however, on Ubuntu it drops as soon as I start downloading anything!!! This is what puzzles me and next thing is my computer doesn't show up in the DHCP client list even when I'm connected!!!

---

### Post by sfled on 2010-12-07
If I may suggest, the F5D7230-4 has a couple of default settings that may be causing the issue. If I'm not mistaken, they are all in the "Wireless" section of the router's admin interface.

1) Turn 'Protected Mode' off.
2) Turn 'Turbo Mode' off.

In my case, since I no longer use 801.11b, I set the router to 801.11g. I also no longer stealth the SSID. The router is set to WPA/WPA-2 and I use MAC address filtering for security. The Firewall on the router is on.

This is a mixed Win/Mac/*nix network.

Hope this helps.

Ed

> **rakusson said:**
> hi,

I am using Hardy Heron and connect to the Internet through Belkin wireless router F5D7230-4. I have experienced a problem recently. When I try to download something from ubuntu, surprisingly, the network connection drops and I can no longer use Internet! 

Another surprising thing is that my Router's "DHCP client list" doesn't shows my computer!!! (I have attached screen shot, my computer name is Ramesh-T40 and is not in the list but I am still connected and using Internet, even when posting this message!!!). What could be the problem? Though the connection drops periodically in WinXP as well but never on downloading and I can see my computer name in the list.

What could be the problem and possible solution?

---

