---
title: "BCM4318 [AirForce One 54g] won't connect to any network"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by AlcoJaguar on 2007-02-21
I'm new to the forums as I only installed Ubuntu about three days ago but I've already found them an invaluable tool. I recently followed the [tutorial by nickm about Broadcom Wireless NICs]("http://ubuntuforums.org/showthread.php?t=185174") and all seemed to go smoothly, I had no problems with the tutorial nor getting my card detected and configured with gnome-network-manager but I seem to have trouble connecting to networks even when they have been detected.

I stripped all security out of my router (I removed MAC filtering, took off WEP, and reset it to its default channel) and have been attempting to connect to it using my Dell Latitude C850 with a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) (pcmcia card). I get all the way to the point of gnome-network-manager attempting to connect to the network but then it times out and falls back to my wired connection. 

Before I began the tutorial I blacklisted ndiswrapper and commented out my /etc/network/interfaces file of all entries except loopback. My card had already been detected by Ubuntu and I had met all the other mentioned prerequisite in the tutorial (actually, I use 6.10, not 6.06 but I didn't see a problem with the process).

Here are some outputs for your reading pleasure

lspci | grep Broadcom\ Corporation
```
07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

iwconfig     (edited for brevity, only showing my card, eth1)
```
eth1      IEEE 802.11b/g  ESSID:"Wulfgang"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:16:B6:B2:1D:70
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep bcm
```
bcm43xx               127252  0 
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac
```

Everything seems to be in good working order. I'm connecting to a router sitting next to me that , like I mentioned before, is on channel 6 (2.437 GHz), has no encryption, is broadcasting its ESSID, and has no MAC filtering. The router is also set to mixed so it'll pick up both G and B.

Anyone see anything out of place? Its been a long time since I last used any linux distro, and I come from Debian. I've never actually used wireless on a linux box before either, I've heard the horror stories :) .

---

### Post by AlcoJaguar on 2007-02-21
Also If anyone requires any additional information or command outputs feel free to ask. I appreciate any help I can get, I've spent many hours on this problem (though not as many getting direct rendering on this laptop...)

---

### Post by AlcoJaguar on 2007-02-21
Bump. Fell off most recents...

---

### Post by AlcoJaguar on 2007-02-21
Made a little discovery in the 4 hours since my original post. When I disable network-manager through gnome-network-manager I can connect to my network with the Network Monitor that came with Ubuntu. Albeit this is with no WEP encryption which I'm about to go test out. Anyone know if Network Monitor and network-manager fight over control of my wireless NIC (I had originally disabled my wireless card in Network Monitor).

I disconnected and tried re-enabling my WEP with no luck. I use 128-bit and it seems like Network Monitor allows you to use such keys and it looks as if it also finds the AP and starts communicating, but after a quick iwconfig I find that I have an excessive amount of 'Rx invalid crypt: 92'. I'm out of options on those route. Either I use Network Monitor and not get encryption, or I use gnome-network-manager and get encryption, but lose the ability to acquire and address from the AP.

---

### Post by AlcoJaguar on 2007-02-21
I got it working. The software doesn't like 2nd, 3rd, or 4th generated keys off of passphrases (even if you type the key in directly and never use the passphrase). I switched the key on my router back to the 1st and it immediately started working. At least I didn't waste anyone else's time, seems I've just been talking to myself here.

---

### Post by 22350 on 2007-02-22
i would love to know how you got this card working:

[http://ubuntuforums.org/showthread.php?t=366819](http://ubuntuforums.org/showthread.php?t=366819)

---

