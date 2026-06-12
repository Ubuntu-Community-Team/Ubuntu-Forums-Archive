---
title: "WUSB54G and Ndiswrapper"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by Darkdelusions on 2007-06-18
I am currently trying to use my WUSB54G with Ndiswrapper 1.34. The hardware is detected and working sort of. I use WPA2 on my router and have setup WPA supplicant use the instructions above. However when i do a /etc/init.d/network restart then do  a iwconfig it will not assign my SSID. If i turn off all encryption it will allow me to set my ssid and connect. 

Another thing I tried was turn off my WPA and just setup mac filtering and commented out all the lines for WPA in the interfaces files. But I am still unable to set my SSID.

I was thinking of just going out and getting a Linux native supported card however i thought I would give it one last shot here. I was going to try the prism54usb native drivers but I have read wpa is not supported with those. 

Any help would be greatly appericated. 

Distro Fiesty Server (Running MythTV)

Interfaces: 

```

auto wlan0
iface wlan0 inet static
address 192.168.168.220
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext #I have also tryed the ndiswrapper settings
wpa-ssid delusional
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk Hexkeyhere
```

---

### Post by kevdog on 2007-06-18
Please post:

ndiswrapper -v
ndiswrapper -l

What if you just try using WPA1 instead of 2??

Lastly you said you set up wpasupplicant??  What do you mean??  Ive seen many different setup how to use this package, as far as making .conf files, etc.  but not all ways are interchangeable.

---

### Post by Darkdelusions on 2007-06-18
When I ment setup wpa sup I ment using the Sticky walk threw for WPA. 

Also the Drivers are the lastest drivers off the linksys site and version of ndiswarapper is whatever in the repos. I thought it was it was 1.34. But i will verify that when i get home for sure....

---

### Post by wieman01 on 2007-06-18
What version of WUSB54G have you got? Mine is a WUBS54G V4 (Ralink) and it works via "ndiswrapper" and the latest Linksys driver. WPA2 is no problem at all given that you have installed "ndiswrapper" and deployed the Windows driver correctly.

What does a...
> sudo iwlist scan
...yield?

---

### Post by Darkdelusions on 2007-06-18
I am using a WUSB54G v1 and I am able to see my router along with many other when i do an iwlist wlan0 scan. So i know the card is working semi correctly...... Also I am dead positive it used the prisim54 chipset (which is now blacklisted)

---

### Post by kevdog on 2007-06-18
Maybe the ndiswrapper repo version works for you, but I never found that to work for me.  If you do
ndiswrapper -v

and get no errors, then there probably isnt a problem.

As far as the driver issue for your card, I would look specifically on the ndiswrapper sourceforge website and download the driver they recommend. It might be what you have, but in many cases its a different driver.  All drivers listed on their website have been tested with ndiswrapper and are known to work.  

As far as wpasupplicant setup I assume you are referring to Weiman's sticky.

---

### Post by Darkdelusions on 2007-06-18
```
ndiswrapper -l
   Device (1915:2234) present (alternate driver: prism54usb)

```

*** I blacklisted the prism54usb

```
ndiswrapper -v 
driver version 1.38\

```

iwlist Scan results
```

Cell 02 - Address 00:18:F8:5D:72:AC
Essid: "delusional"
Protocol: IEEE 802.11b
Frequency 2.437 GHZ (channel 6)
Quality 39/100 Signal level -71 dBm Noise Level: -96 dBm
Encryption Key: off
Bit Rates 1 Mb 2Mb 5.5mb 11 mb 6mb
9mb 12 mb 18mb 24 mb 36mb
48 mb 54 mb
Extra:bcn_int=100

```

**** Note Right now WPA is turned off for trouble shooting reasons

Interfaces Files

```
auto wlan0
iface wlan0 inet static
address 192.168.168.220
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext #I have also tryed the ndiswrapper settings
wpa-ssid delusional
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk Hexkeyhere


```

---

### Post by Darkdelusions on 2007-06-19
Any Suggestions?

---

### Post by wieman01 on 2007-06-19
Is the Windows driver capable of WPA? The script looks fine.

If WPA2 fails, try WPA1 instead:
> auto wlan0
iface wlan0 inet static
address 192.168.168.220
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid delusional
wpa-ap-scan 1
wpa-proto [COLOR="Red"]RSN WPA[/COLOR]
wpa-pairwise [COLOR="Red"]CCMP TKIP[/COLOR]
wpa-group [COLOR="Red"]CCMP TKIP[/COLOR]
wpa-key-mgmt WPA-PSK
wpa-psk Hexkeyhere
"wext" is the right driver.

---

### Post by Darkdelusions on 2007-06-19
wieman01

You might be on to something about the WPA2 support.... Below is what I pull of Linksys Website


> Linksys, A Division of Cisco Systems, Inc.

Product:               WUSB54G

Classification:        Driver Release History

Release Date:          09 / 03 / 04

Last Driver Version:   v1.0.8.0 (WinME, Win2000 and WinXP)
Last Monitor Version:  v2.0
__________________________________________________________________________

Instruction:
Please make sure to un-install the old monitor from your PC before installing 
the new one.
__________________________________________________________________________
- Changed the WLAN Monitor Format and version to v2.0
- Supports Linksys Wireless Network Monitor under Windows XP.
- Supports PSK (WPA Personal) and PSK+RADIUS (WPA Enterprise).
- Fixed some issue regarding connection of WEP security.

Driver Version v1.0.8.0
Monitor Version v1.1
- Windows Logo certified for Windows XP and 2000.
- Adds WPA (Wi-Fi Protected Access) support under Windows XP.
- To support Windows ME.
- Fixed the memory leak issue.
- Changed the WLAN Monitor version to v1.1

Driver Version v0.6.0.0
Monitor Version v1.05
- First Released.


---

### Post by Darkdelusions on 2007-06-19
This Thread is sloved.

After switching to WPA from WPA2 we have network connectivity

Thanks to everyone for there help and pointing out the one over looked aspect

---

