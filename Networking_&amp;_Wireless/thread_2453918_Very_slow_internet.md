---
title: "Very slow internet"
date: 2020-11-19
forum: Networking &amp; Wireless
---

### Post by alphardvb on 2020-11-19
Goodmorning,

I have a question which can be ask at 2 communitys so I will do that.
I am downloading Emby Server. Last week I downloaded it within the minute. because of some other errors I formatted my sd-card en installed Ubuntu again, this time version 20.10. now I download and it takes more than 20 minutes. Is something wrong with my internet connection, or is something wrong at Emby? Also another question: wpa_supplicant.conf. I thought that was a file where you could set up your wifi. but now I open it, and its empty.

I hope to hear from you soon.

Wkr,

Alphard

---

### Post by grahammechanical on 2020-11-19
Please run these two commands

```
sudo apt update
sudo apt upgrade
```

The printout will tell you how fast the download is happening. It could be in mega bytes per second (mB/s) or kilo bytes per second (kB/s). If it is kilo bits per second (kb/s) or only bits per second (b/s) then the internet connection is really slow.

I had very slow download speeds recently that lasted for weeks. I use a landline and there was interference (noise) on the line that forced network manager to make repeated requests for the sending computer to re-send the data, In this way the download speed dropped from 800 kB/s to 20 kB/s and even 20 b/s.

It would help if you told us about your internet connection. If is it landline? Is through a mobile connection? Fibre optics? How are you connecting to the router? Ethernet? Wi-Fi? Is the router shared by other devices (computers)?

If we open system settings>Network and are using an ethernet connection to the router we will find out the connection speed of the ethernet adapter in the computer. If we select Wi-Fi we will find out the connection speed of the Wi-Fi adapter in the computer. This information could be useful for comparison purposes.

Regards

---

