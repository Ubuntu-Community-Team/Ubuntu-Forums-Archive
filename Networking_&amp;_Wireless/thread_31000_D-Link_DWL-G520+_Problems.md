---
title: "D-Link DWL-G520+ Problems"
date: 2005-05-01
forum: Networking &amp; Wireless
---

### Post by dhanjel on 2005-05-01
Hi,

I have a D-Link DWL G520+ pci wireless card ([http://www.dlink.com/products/?sec=0&pid=12)](http://www.dlink.com/products/?sec=0&pid=12)), hardware version A3, firmware version 2.04 with the Texas Instruments chipset and I can't get it to work in Ubuntu.

The card is detected and wlan0 is created, but if I use iwlist to scan for my network on the correct channel, nothing is found.

I can with the network configuration tool in Gnome set up a static ip adress and get a signal strength, so I assume that it is connected to the network. But nothing else works. I don't have WEP encryption enabled at the moment, so that shouldn't be a problem.

Does anyone have any suggestion on how to solve this?

---

### Post by dhanjel on 2005-05-02
I found a driver for this chipset (Texas Instruments ACX111) at [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) , but I neved managed to install them. 

Has anyone successfully installed and configured this chipset?

---

### Post by kamstrup on 2005-05-02
According to this section

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

You should use ath_hal or acx100... Are you sure acx100 is not available in universe/multiverse/restricted?

---

### Post by kamstrup on 2005-05-02
Well just searched the =?*£$ out of the repositories... It isn't there. Then there's definitely wrong information in the WIKI... What a shame.

Is it 530+ or 520+ ?

About compiling installing... Do you have kernel sources installed?

---

### Post by dhanjel on 2005-05-02
[QUOTE=kamstrup]Well just searched the =?*£$ out of the repositories... It isn't there. Then there's definitely wrong information in the WIKI... What a shame.

Is it 530+ or 520+ ?

About compiling installing... Do you have kernel sources installed?[/QUOTE]

Sorry, it's the 520+. I have the ath_hal drivers loaded and configured, I get a signal strenth so it must have some connection to the router. But DHCP or static ip adress does not work. It sends data but never recieves any.

---

### Post by kamstrup on 2005-05-02
What have you done trying to get the acx100 driver working? Is it compile, install or other errors you get?

---

### Post by dhanjel on 2005-05-02
[QUOTE=kamstrup]What have you done trying to get the acx100 driver working? Is it compile, install or other errors you get?[/QUOTE]

I will try again tonight and see what happens.

---

