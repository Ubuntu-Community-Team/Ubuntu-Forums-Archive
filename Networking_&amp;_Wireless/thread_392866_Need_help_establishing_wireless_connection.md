---
title: "Need help establishing wireless connection"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by cknight on 2007-03-25
Hi folks,

I can't seem to get Knetworkmanager to establish an unsecured wireless connection to my router.  It detects the connection (the SSID shows up in the list), but on attempt to connect it stalls at 28% attempting to configure the device (a netgear WG311T wireless pci card in this case). 

To step back a bit, I can establish an unsecured connection using the Wireless Assistant which came with Kubuntu.  Unfortunately, I've been unable to establish a WEP or WPA connection using Wireless Assistant, so I thought I'd try Knetworkmanager as I was told it might be better for this type of connection.

The strange this is, once Knetworkmanager fails to connect, this causes the Wireless Assistant to fail to connect too.  I have to reboot before the Wireless Assistant is able to connect again.

Any other network tools out there which might help me with WEP or WPA?  Wireless Assistant only seems to support WEP and fails to connect when I attempt to use it.

Can anyone help?  Much appreciated.

---

### Post by handaxe on 2007-03-25
An alternative network connection manager is Wicd.  Some folk have found success with it.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by entering /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper) as a startup proggie (I am a long term Gnomer and KDE is a mystery to me...)

See how this goes. Good on different encryption types, and makes WPA partic easy You might uninstall any other managers first.

HA

---

