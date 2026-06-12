---
title: "Wi-Fi disabled even after &quot;Enable Wi-Fi&quot; is checked"
date: 2017-09-06
forum: Networking &amp; Wireless
---

### Post by ferronato on 2017-09-06
On startup the option "Enable Wi-Fi" is always unchecked but even after checking it nothing changes and I can't list/connect on any wireless network.

wireless-info: [http://paste.ubuntu.com/25478225/](http://paste.ubuntu.com/25478225/)

---

### Post by jeremy31 on 2017-09-06
It shows it has a hard block on the wifi, is there a switch to enable/disable wifi or an option in BIOS to enable?

---

### Post by johndough2 on 2017-09-07
Hi

The WiFi should be looked at in the BIOS just to be sure it is enabled, although I believe it is.

The last few lines of the pastebin show that the ethernet is running at 100mbs and connected to sky2 possibly?
But no indication of the WiFi coming up, hence the double check with the BIOS.
You dont have a physical slide switch on the side of the machine do you?

Tx-Power=off  That seems so obviously wrong, and somewhere in a config/properties should be a setting to make it show as at least on, and preferably at maximum.

Try a different Network Manager, perhaps Wicd, ([https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)) has some commands to install and help, like this...
Open up a Terminal and execute the following commands:
```

    First, we need to download the latest NetworkManager, in case we need to reinstall if WICD doesn't work:

        sudo apt-get install -d --reinstall network-manager plasma-widget-networkmanagement 
    Then, we need to install WICD:

        sudo apt-get install wicd-kde 

    Next, we uninstall NetworkManager:

        sudo apt-get remove plasma-widget-networkmanagement network-manager 

    After everything is confirmed to be working (it's best to check this after rebooting), you can remove config files for NetworkManager:

        sudo dpkg --purge plasma-widget-networkmanagement network-manager


```

You perhaps have not set the country code, and there are 4 profiles for WiFi
id=VIVO-A148
id=Fronter
id=VIVO-A148 1
id=Fronter 1

So is one of those yours?

It does suggest a WiFi is installed and running, but just lost, no name or direction for connection.

If in doubt please ask.

---

### Post by chili555 on 2017-09-07
> Tx-Power=off That seems so obviously wrong,If the radio is turned off by the hardware switch or key combination, then that's exactly what we'd expect; the transmit power is zero.> Try a different Network Manager, perhaps Wicd, ([https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)) has some commands to install and help, like this...
Open up a Terminal and execute the following commands:If the switch is set to disable wireless, then installing Wicd isn't going to change it at all.

The fact that there are existing wireless profiles suggest that you have been connected successfully previously. You just need to find and switch that switch.

---

