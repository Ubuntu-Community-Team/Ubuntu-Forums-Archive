---
title: "[SOLVED] iwconfig wlan0 essid not working at all"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by mnegrete on 2007-06-28
Hi all,

I have a little problem with my network; I have a box with Ubuntu 7.04 and a Trendnet TEW-423PI card (PCI, chipset 88w8335 from Marvell) which I installed with ndiswrapper 1.47 using the drivers on the CD (also tried with the drivers from several others vendors just for test if this was the problem).

The card is up and if I run ```
iwlist wlan0 scan
``` it lists all of the AP's around, included mine. I've edited /etc/network/interfaces with
```
iface wlan0 inet static
wireless-mode managed
wireless-essid negrete
wireless-key ***
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254
```
but yet I cannot connect to my AP.

If I run ```
iwconfig wlan0 essid negrete
``` it doesn't throws any error but yet I cannot connect :(

Also the bare comand ```
iwconfig wlan0
``` shows no SSID associated.

The output for dmesg | grep wlan0
```
(...)
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
ADDRCONF(NETDEV_UP): wlan0: link is not ready
(...)
```

Any ideas for this problem?

Thanks in advance

---

### Post by mnegrete on 2007-06-28
At least can anyone give me a link or something?

---

### Post by kevdog on 2007-06-28
Can you list the following:
ndiswrapper -l

Just want to make sure multiple drivers are not installed.

You are trying to use WEP.  Does the connection work if the network is unencrypted???

What exactly does 
iwlist scan 
show??? Is the quality greater than 0??

---

### Post by mnegrete on 2007-06-29
Hi kevdog, thanks for your reply and sorry for not answering but I've been working a lot :(

> **kevdog said:**
> Can you list the following:
ndiswrapper -l
```
mrv8335 : driver installed
        device (11AB:1FAA) present
```
> 
Just want to make sure multiple drivers are not installed.

You are trying to use WEP.  Does the connection work if the network is unencrypted???
```
No, it doesn't work either using WEP or open
```

> What exactly does 
iwlist scan 
show??? Is the quality greater than 0??
```
It lists 13 cells, the one I want to connect says:
Cell 05 - Address: **:**:**:**:**:**
          ESSID:"negrete"
          Protocol:IEEE 802.11g
          Mode:Managed
          Frequency:2.437 Ghz (Channel 6)
          Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
          Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                    9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                    48 Mb/s; 54 Mb/s
           Extra:bcn_int=100
           Extra:atim=0
```

Thanks again

---

### Post by mnegrete on 2007-06-30
Hi kevdog, I've already solved the issue, at this time I don't remember what I did but maybe tomorrow I will post the steps.

Thanks again

---

### Post by chtse.starhub on 2008-04-27
Hi,

iwconfig only works in certain sequence. for my case, it is:

iwconfig wlan0 key off
iwconfig wlan0 mode ad-hoc
iwconfig wlan0 essid (Your wireless router broadcast)
iwconfig wlan0 key restricted (WEP Key)
iwconfig wlan0 mode Managed

keep on trying! ;-)

Jon

---

