---
title: "DWL-650M PCMCIA Wi-Fi Card Feisty WiFi Troubles"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by GlitchCog on 2007-09-08
I've got a D-Link DWL-650M PCMCIA card ([http://support.dlink.com/products/view.asp?productid=DWL%2D650M](http://support.dlink.com/products/view.asp?productid=DWL%2D650M)) for a Dell Inspiron 8200 notebook running Feisty Fawn. The wireless networking worked perfectly with this exact computer and card with a stock Edgy install (which crashed a good bit for me, so I'm not keen on reverting back to it for wireless functionality) and also still works perfectly on my Windows XP partition. When I switched to Feisty, it didn't even recognize or power the card. I checked the [hardware wiki list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"), and there are a bunch of D-Link DWL-650 cards that people say work, but there seems to be lots of different types of this card including the 650+, 650K and L, 650 plain, and others. Anyhow, the 650M isn't listed as either working or not working, so I'm hoping there's still a chance and I'm just too new at this sort of thing to fumble my way through it.

So far I've installed the Windows driver from the D-Link support page with ndiswrapper:

$ ndiswrapper -l
netr33x : driver installed
        device (10EC:8180) present (alternate driver: r818x)

and I've blacklisted some stuff that I've read conflicts with this card in this and other forums (/etc/modprobe.d/blacklist):
blacklist r818x
blacklist r8187
blacklist acx
# from [https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L?highlight=%28WifiDocs%2FDevice%29)
blacklist ieee80211_rtl
# from [http://ubuntuforums.org/showthread.php?t=429547](http://ubuntuforums.org/showthread.php?t=429547)
blacklist orinoco_cs

and I've tried the instructions in the last post of this thread: [http://ubuntuforums.org/showthread.php?t=429547]("http://ubuntuforums.org/showthread.php?t=429547") which involved hex editing .ko files and some other crazy stuff that didn't seem to do anything for me. Oh, and I tried to do some stuff with orinoco_cs because the wiki list said the plain 650 works fine if you've got that PCMCIA package installed. That didn't do anything either.

Right now I've got the card powered/blinking and iwconfig reveals that wlan0 exists, but if I try to scan for networks I get nothing:
$  iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any attempts to manually 'iwconfig wlan0 essid interweb' or doing a manual configuration with NetworkManager don't seem to have any effect. Does this mean I'm just out of luck with a driver that doesn't work with Feisty, or is there something else I can try?

Thanks for reading through my problem. If anyone has a suggestion for what I should try now, I'd be thankful to listen as I'm all out of ideas.

---

