---
title: "Wireless acting weird..."
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by TheBloodyMushroom on 2006-07-30
Hi,
My wireless internet is being weird...I installed the drivers using ndiswrapper and when I run ndiswrapper -l it tells me driver installed, hardware present (or whatever it says). I configured my WEP Key with the Hex, I setup the static IP like its supposed to be. I activated the wlan0. My internet worked one night, but the next day when I booted, it didn't. It hasnt worked since. I know the router and stuff is fine because I'm using it right now on Windows. Its the Compaq HNW-200 11Mbps wireless USB. 

Also, I've heard about running network manager, but when I run ```
sudo apt-get install network-manager
``` it tells me that it can't find the package. I can't seem to get it installed. Is there anyway to download the package on Windows, and copy it and install it and what not in Linux? I'd really like to use network manager, but I can't get it installed.

---

### Post by Titus A Duxass on 2006-07-30
For network manager have you got the correct repositories in your sources.list?

What is the output of:
iwconfig
What is in your /etc/networking/interfaces?

---

### Post by TheBloodyMushroom on 2006-07-30
> **Titus A Duxass said:**
> For network manager have you got the correct repositories in your sources.list?

I'm not sure, how do I check?

> What is the output of:
iwconfig


```
"lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"okuwlan"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:E8AD-F8F6-E543-8CAF-8A03-3BAF-20   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions."

```


> What is in your /etc/networking/interfaces?

```
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


iface wlan0 inet static
wireless-key E8ADF8F6E5438CAF8A033BAF20
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0
```

---

### Post by TheBloodyMushroom on 2006-07-30
Well, after staying up all night, and finding Wifi-Radar...I..finally got my internet up and running. Thank you for trying to aid me, though.

---

