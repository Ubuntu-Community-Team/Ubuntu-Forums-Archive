---
title: "WUSB300N crashing on connect"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by jakegadget on 2009-10-18
Hello everyone.
I just got Ubuntu. I installed etc etc. Using google i found and installed drivers for the WUSB300N wireless adapter. Heres the problem. When I connect to the network, the network connections icon switches to the connecting animation with the little dots. If i click on it, Ubuntu crashes. If I try to run Firefox, Firefox crashes. If i try to run a command in Terminal, it just goes to a blank line and does nothing. Thanks in advance,
-Jake

---

### Post by coldReactive on 2009-10-18
According to the help,

> Used ndiswrapper 1.9 to install driver then had to use ndisgtk's "Configure Network" button to manually select the wireless network's SSID, change encryption to WEP (although, in fact there is no security set on the router) and set DHCP - seemed to only work with these particular attributes set. Downside of ndiswrapper is no network feedback/info from the Network Manager notification area icon on signal strength, etc.

**Drivers supplied by linksys appear to be buggy (dropping connection, etc)**. The best drivers for this particular chipset appear to be the ones provided for the Netgear WN111v1. Currently, I've got it running using the earliest version of the drivers; only shows up after marking the 'show all versions' checkbox. Once these are installed under windows, the drivers (netmw245.inf and Mrvw245.sys files) can be found in c:\windows\inf\wn111 . 

[Source](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB300N)

---

### Post by jakegadget on 2009-10-18
Thanks for the prompt reply. Where would one go to find these drivers? And how would I install them?

[EDIT:] This post here is exactly what my problem is:
[http://ubuntuforums.org/showthread.php?t=1116364](http://ubuntuforums.org/showthread.php?t=1116364)

---

