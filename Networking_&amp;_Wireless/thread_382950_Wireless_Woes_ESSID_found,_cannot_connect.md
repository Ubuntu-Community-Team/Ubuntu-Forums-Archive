---
title: "Wireless Woes: ESSID found, cannot connect"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by nicholas.Platt on 2007-03-12
I recently purchased a wireless card from [www.newegg.com](www.newegg.com), and I'm trying to install it. I'm a very new Linux user, but I'm also interested in its abilities. The best way to learn about them is through the internet, obviously, but I'm having trouble getting that set up.

The card I bought is a [D-Link DWLG510,](http://www.newegg.com/product/product.asp?item=N82E16833127145). The card is capable of working, according to the [ndiswrapper list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) (see section D, #15). I've downloaded the 2.11 driver from [www.dlink.com](www.dlink.com), and have successfully installed both ndiswrapper and the driver onto my computer.

Unfortunately, I'm unable to connect to the internet.
My /etc/network/interfaces file reads as follows:
```

#  This file describes the network interfaces available on your system
#  and how to activate them. For more information, see interfaces(5).

#  The loopback network interface
auto lo
iface l0 inet loopback

#  The primary network interface
auto ath0
iface ath0 inet dhcp
     wpa-driver  wesk
     wpa-conf  managed
     wpa-ssid  secrethouse
     wpa-ap-scan  1
     wpa-proto  WPA RSN
     wpa-pairwise  TKIP CCMP
     wpa-group  TKIP CCMP
     wpa-key-mgmt WPA-PSK
     wpa-psk ......

```

I'm not really sure of what other information you need in order to help me, but if you can tell me what it is and how to find it, I'll be sure to give it to you.
As I said, the card is functioning (LEDs are lit up), and when I run iwlist scan my ESSID shows up correctly. I believe the my encryption key settings are incorrect, but I'm not sure of how to solve the problem. The wireless router is located inside my house, and I'm the administrator of sorts, so I can get you any information about that as well.

I greatly appreciate your help. =)
Thanks a lot.

---

### Post by handaxe on 2007-03-15
[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper).

See how this goes. Good on different encryption types. You might uninstall any other managers first.

---

### Post by nicholas.Platt on 2007-03-15
My apologies, I should've let you guys know that I was able to get the Internet working after completing a full install of Ubuntu. I had to "borrow" some ram from some old computers at my school, but they were going to the dumpster anyway. With Ubuntu, the card was recognized right away, and I was able to connect to my router after installing **Gnome Network Manager:** [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

Thanks for the reply, though. =)

---

