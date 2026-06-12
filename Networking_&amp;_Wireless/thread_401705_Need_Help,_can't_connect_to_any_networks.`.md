---
title: "Need Help, can't connect to any networks.`"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by huzelj on 2007-04-04
Hello,

I have followed instructions for installing my BCM4306 wifi card with fwcutter, everything seemed to work, however I can see all of the wireless networks but I can not connect to any of them, when I try it takes a long time to be assigned an IP address and it fails.

When I type in iwconfig I get:

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon

and with **iwlist eth1 scan**


eth1      Scan completed :
          Cell 01 - Address: 02:12:F0:03:56:4B
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-46 dBm  
                    Extra: Last beacon: 4212ms ago

I am running Ubuntu 6.10, from a fresh install I set up my wireless card. But now I am at my wits end, it is just taunting me!

Any help would be really appreciated.

Thanks,

Jake

---

### Post by Floppyjoe on 2007-04-04
> eth1 Scan completed :
Cell 01 - Address: 02:12:F0:03:56:4B
ESSID:"linksys"
Protocol:IEEE 802.11bg
Mode:Ad-Hoc
Channel:11
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality=100/100 Signal level=-46 dBm
Extra: Last beacon: 4212ms ago


If this is your router then try changing the mode on the router to something other than ad-hoc.

---

### Post by huzelj on 2007-04-04
Nope its not my router, I am just trying to connect to any open wireless network, I have checked and just tried connecting to another one (which isn't listed as Ad Hoc) but when I do iwlist eth1 scan, it still says ad hoc.

Do I need to manually set my card to connect normally? If so is there a command that I can type to do so?


Jake

---

### Post by Floppyjoe on 2007-04-04
> **huzelj said:**
> Nope its not my router, I am just trying to connect to any open wireless network, I have checked and just tried connecting to another one (which isn't listed as Ad Hoc) but when I do iwlist eth1 scan, it still says ad hoc.

Do I need to manually set my card to connect normally? If so is there a command that I can type to do so?


Jake

The /etc/network/interfaces file is where I would enter manual connection information if that is the way you want to go.
```
sudo gedit /etc/network/interfaces
```

---

### Post by huzelj on 2007-04-04
Ok,

What should I put in there for manual connection info? Will that limit me to connecting to only one wireless network without updating the information in interface file?

When I have opened it this is all that is there,



auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Thanks for your help, I am a bit new to all of this,


Jake

---

### Post by Floppyjoe on 2007-04-04
If you are using a mobile computer like a laptop you might want to download network-manager and use that to control your networks. Then you can move from one network to another using DHCP.

---

### Post by huzelj on 2007-04-04
Sorry,

I guess I should have mentioned, I am using network manager and I have tried wifiradar as well, but neither allow me to get connected to any wireless networks, it seems I fail to be assigned an IP address.



Jake

---

### Post by Floppyjoe on 2007-04-04
> **huzelj said:**
> Sorry,

I guess I should have mentioned, I am using network manager and I have tried wifiradar as well, but neither allow me to get connected to any wireless networks, it seems I fail to be assigned an IP address.



Jake

Are all your network interfaces deactivated in System/Administration/Networking?
This is required for network-manager to work properly in 6.10.

---

### Post by huzelj on 2007-04-04
My wireless was disabled already, so I disabled my wired connection as well and then tried to connect to a wireless network and only got "Attempting to connect to..."

I had to enable the wired connection again to establish a wired connection.



Jake

---

### Post by Floppyjoe on 2007-04-04
I would make sure only to use one network changing program at once because they tend to conflict with each other. You should not have to activate your ethernet connection if you are using network-manager with the 6.10 OS.

---

### Post by huzelj on 2007-04-04
I removed WifiRadar, disabled my wired connection, and restarted my computer, could only view wireless networks when I clicked on Network Manager, but I could not connect to any of them, some of them were WEP secured, and it did prompt me for a key, which is a good sign, but others that were not secured that were free public wifi I could not establish a connection to.

As well, I could not get connected afterwords without enabling my wired connection, before enabling it I tried firefox but it didn't work.


Jake

---

### Post by Floppyjoe on 2007-04-04
> **huzelj said:**
> I removed WifiRadar, disabled my wired connection, and restarted my computer, could only view wireless networks when I clicked on Network Manager, but I could not connect to any of them, some of them were WEP secured, and it did prompt me for a key, which is a good sign, but others that were not secured that were free public wifi I could not establish a connection to.

As well, I could not get connected afterwords without enabling my wired connection, before enabling it I tried firefox but it didn't work.


Jake

Some wifi networks that appear to be open are protected by mac address filtering.

---

