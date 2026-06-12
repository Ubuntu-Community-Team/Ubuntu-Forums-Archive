---
title: "wireless card not found"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by willtell on 2007-05-09
I just started using ubuntu but I can't get it to recognize my wireless card.  I have a netgear WG311 v3 and it is among the supported cards, so "the list" says.  When I run lspci and lspci -n, it found the card.  When I ran 
sudo lsmod | grep WG311v3 nothing appeared.  I've tried to install ndiswrapper but it says that it must download part of the file in order to get it to work, but it's not connected to the internet obviously, so it doesn't download it.  Any suggestions or help is greatly appreciated.

---

### Post by chili555 on 2007-05-10
I don't see a list that says version 3 is fully supported, can you please refer us to it?

lsmod would show the module, or driver that's loaded; it's never the name of the device, although it may be somewhat related to the chipset for wireless devices. 

I believe ndiswrapper is on the install CD. Please try these commands in a terminal:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```Apt will pull in a few dependencies which you should accept and it will complain that it cannot reach the internet repositories which you can ignore.

---

### Post by willtell on 2007-05-10
I think the list I was looking at is the list of cards that work with NDISwrapper.  And I found it on
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

I'm going to try what you said right now. Thanks.

#
Netgear WG311 v3 (Marvell 88w8335 Libertas)

    *
      Chipset: Marvell 88w8335 Libertas 54Mbps Wireless Interface
    *
      pciid: 11ab:1faa
    *
      Driver copied from [http://kbserver.netgear.com/products/WG311v3.asp](http://kbserver.netgear.com/products/WG311v3.asp)
    *
      From Initial Release 6.20 MB May 16,
    *
      Running Mandriva Free 2007 DVD
    *
      Program Computer Configuration - Network and Internet-Cofiguration New Device
    *
      Works Great
    *
      Trabaja muy bien

---

### Post by chili555 on 2007-05-10
Glad it's working for you! > Running Mandriva Free 2007 DVDPlease be sure to tell the folks over on Mandriva forums to consider Ubuntu because of its helpful community!:)

---

### Post by willtell on 2007-05-10
I was finally able to get it working from this how to.  Thanks for your help.

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

---

