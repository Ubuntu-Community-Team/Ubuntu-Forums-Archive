---
title: "Wireless Config: forced to use ethernet cable?! Please Help!"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by BoJaNgLes19 on 2008-04-05
This may sound stupid but I dont believe my wireless card is supported.

I have a Trendnet 802.11g TEW-424UB Wireless USB and it, according to [http://linux-wless.passys.nl/query_chipset.php?chipset=Sis](http://linux-wless.passys.nl/query_chipset.php?chipset=Sis) , is unsupported and does not work for linux.  

Does this mean that i have no other options as far as drivers and such to get this to work?

Id really rather not run the ethernet cord all the way up the stairs, its starting to bug me.  Any suggestions would be great, as i'd rather not buy another wireless card :/

I also referenced these threads/stickies for help:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

The third link here gave me this info about my specific usb wifi card:

Card: Trendnet TEW-424UB 802.11g Wireless USB Adapter

      Chipset: sis163u (Silicon Integrated Systems Corp)
      pciid: 0457:0163
   
      Driver: Latest driver for sis163 from [http://www.sis.com](http://www.sis.com)
   
      Other: Works with WEP, WPA+TKIP and WPA+AES; tested with ndiswrapper version 1.13, 1.4 and 1.23, it seems it doesn&#8217;t work with 1.24 and higher.
   
      Other: As of 21 Feb 2007, works correctly using drivers from the CD with ndiswrapper version 1.37.

Can anyone tell me what this all means?  Im new to linux as far as setting up networks and such so help would great.  Thanks in advance :)

---

