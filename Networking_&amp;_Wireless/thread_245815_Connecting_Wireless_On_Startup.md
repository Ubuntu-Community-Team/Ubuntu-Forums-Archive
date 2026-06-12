---
title: "Connecting Wireless On Startup"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by dpm on 2006-08-28
I've got a D-Link AirPlusG+ (DWL-G650+) PC Card network card with the Texas Instruments ACX 111 54Mbps Wireless Interface (ac111 CardBus/PCI) chipset. I am using the open source acx driver ([http://acx100.sourceforge.net)]("http://acx100.sourceforge.net%29"), officially distributed in dapper. So far -apart from a couple of minor issues- my network connection is working.

However, there is one thing I haven't managed to get working since Breezy, and that's to get the network card to automatically connect to the internet before GNOME is loaded. I always have to wait until the desktop is loaded and then manually associate the card to the access point to get internet connectivity.

For testing purposes, I am not using encryption, so the wireless part of my **/etc/network/interfaces** file looks simply like:

```
  iface wlan0 inet dhcp
  wireless-essid myessid
  wireless-key open
  auto wlan0
``` 
When the startup scripts which configure the network interfaces are executed, the "Link" LED of the network card is lit, indicating that the card is ready, but it seems that the hotplug interface is either ignoring /etc/network/interfaces or taking too long to acquire a dhcp lease from the access point (pure guesses), so the network card is never associated to the access point until I manually do it when the GNOME desktop is loaded.

To "manually" connect I use gtkwifi ([http://www.ubuntuforums.org/forumdisplay.php?f=74](http://www.ubuntuforums.org/forumdisplay.php?f=74) and [http://sourceforge.net/projects/gtkwifi)]("http://sourceforge.net/projects/gtkwifi%29"), which I've got since Breezy. The Breezy version has got a couple of minor issues with Dapper (some icons are not shown, the list of networks is also not shown), but it works fine as far as connecting to networks. BTW, the problems can be solved by downloading the latest version (1.10) of the scripts from CVS.

Anyway, I've also tried to use NetworkManager instead (thinking that being a daemon, it would connect the network card to the access point before loading the desktop), but apart from listing the currently available networks, it doesn't do much. It always fails to connect to any network with errors of the type:

```
  dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
``` 
AFAIK, there is no such path as /com/redhat/... in Dapper. And yes, I uncommented all interfaces in /etc/network/interfaces before using NetworkManager (although it seems to me that this it is not needed nowadays).

Anyway, my questions are: is there any possible way to get a wireless card to automatically connect to the internet before the desktop is loaded? Am I doing someting wrong there?

Any comments/suggestions regarding to the above will be greatly appreciated.

Thanks.

---

