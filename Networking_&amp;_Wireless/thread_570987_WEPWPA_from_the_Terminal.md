---
title: "WEP/WPA from the Terminal"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by GSF1200S on 2007-10-08
Ive been running an open network (router, wireless) for a while now, and Id rather not. Im running KDE core on top of the Buntu 7.04 kernel. I want to set up a WEP or WPA encryption, but after reading multiple posts, it would prolly be better to run WEP, as WPA seems to be very difficult on Linux.

Since this KDE core install, I havent used the network manager or any kind of wireless network connector. Ive just connected through the terminal, as I did when I set up the GUI from the command line install.

For example, to get a list of networks, I type:

```
iwlist scanning
```

To get a list of available networks. Then, I find the unsecured one that I want and type:

```
sudo iwconfig ath0 essid routername
```

Everything works perfect, but what if im trying to connect to a WEP encrypted network- would I type something else? I did

```
man iwconfig
```
-and-
```
iwconfig --help
```
as well as some searches through the forums, but I havent been able to find a solution.

Any ideas out there?

---

### Post by kevdog on 2007-10-08
sudo iwconfig wlan0 essid "network name in quotes"
sudo iwconfig wlan0 key XXXXXX  <----hex key, if you want ASCII its s:ASCII_KEY
sudo dhclient wlan0

thats for wep, wpa is a different animal

---

### Post by GSF1200S on 2007-10-08
> **kevdog said:**
> sudo iwconfig wlan0 essid "network name in quotes"
sudo iwconfig wlan0 key XXXXXX  <----hex key, if you want ASCII its s:ASCII_KEY
sudo dhclient wlan0

thats for wep, wpa is a different animal

Cool.. ill try it out right now. Whats the deal with ASCII? Is that just a variant or an extension to WEP?

Anyways, that was what I needed...

---

