---
title: "Help on the wireless"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by moonhost on 2007-06-06
T60, ThinkPad 11a/b/g/n Wireless LAN Mini-PCI Express Adapter, Ubuntu 7.0.4 (X86_64). 
I did step by step following :
_**[http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)**_

Each step was fine, but the last step toild me "NO SUCH DEVICE"
[B][COLOR="Blue"]
root@myhost:~# modprobe ndiswrapper
root@myhost:~# iwconfig wlan0
wlan0     No such device
[/COLOR][/B]

If you had the wireless card work for you, please let me know how you did that. Thanks!

---

### Post by alexrb on 2007-06-06
> **moonhost said:**
> T60, ThinkPad 11a/b/g/n Wireless LAN Mini-PCI Express Adapter, Ubuntu 7.0.4 (X86_64). 
I did step by step following :
_**[http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)**_

Each step was fine, but the last step toild me "NO SUCH DEVICE"
[B][COLOR="Blue"]
root@myhost:~# modprobe ndiswrapper
root@myhost:~# iwconfig wlan0
wlan0     No such device
[/COLOR][/B]

If you had the wireless card work for you, please let me know how you did that. Thanks!

what does *iwconfig* says?

---

### Post by moonhost on 2007-06-07
> **alexrb said:**
> what does *iwconfig* says?

root@myhost:~# iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

---

### Post by Lukeg on 2007-06-08
Try 'lsmod' to confirm ndiswrapper was loaded.  Did you confirm that the driver was installed with 'sudo ndiswrapper -l'?  These instructions worked fine for me on my t60p (though not devices are recognized by knetworkmanager for some reason).

---

