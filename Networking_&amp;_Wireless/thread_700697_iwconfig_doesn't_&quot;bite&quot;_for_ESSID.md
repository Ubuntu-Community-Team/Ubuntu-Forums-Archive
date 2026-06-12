---
title: "iwconfig doesn't &quot;bite&quot; for ESSID"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by andersw on 2008-02-18
Setup:
Ubuntu 7.10
ndiswrapper 1.52
Wifi card Netgear: WG111v3. using WG111v3 drivers

Tried everthing. Strange thing is that it looks like I can't get iwconfig to set the ESSID.
Doing "iwconfig  wlan1 essid "networkname"" and then directly iwconfig", iwconfig will report back "ESSID: off/any"

So it will never associate with a AP.

One strange thing I see is:
iwconfig -v reports:
iwconfig Wireless-Tools version 29
              Compatible with Wireless Extension v11 to v21
Kernal    Currently compiled with Wireless Extension v22
wlan1     Recommend Wireless Extension v18 or later 
              Currently compiled with Wireless Extension v22


Can this case my problems? If so, any alternative tools to iwconfig to use?

Anders

---

### Post by Whiffle on 2008-02-18
The AP is open, correct?

---

### Post by andersw on 2008-02-19
I use an AP with multi ssid, with two enabled at this moment
One is WEP/64bit key and one is "hidden" but open.

Latest update.
After disabling Networkmanager and installing WIFI-radar doing all configuration form that GUI, status is:
* Can associate with the hidden but open network with setting "mode auto". Problem is that this association will be "converted" to an Ad-Hoc association ???? (I use this SSID for many other computers i my network).  iwconfig will show both ESSID and Alias as the name of my hidden SSID name
Tried both DHCP and fixed IP, but no TCP/IP connection will be enabled over this Ad-Hoc link (ping say no route to host)
If I try to force the mode to "managed", no association will be made.
 
* Can NOT associate with the WEP enabled SSID (tried bot hex and ascii key).
 iwconfig will show ESSID as "any/off" but Alias as the SSID name I specified. 


Anders

---

### Post by andersw on 2008-02-19
No need for any answer anylonger.

I gave up this stick and got myself a linksys wusb54GC.
After some hassle with compiling new RT73 driver from serial monkey, blacklisting modules etc etc I finally got that working instead.

Anders

---

