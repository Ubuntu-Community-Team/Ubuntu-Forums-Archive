---
title: "No 5 Ghz?"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by Martin_Laursen on 2015-05-19
I'm quite new to Lubuntu, and is running it at a Asus 1015PEM.

When looking up the network cards, I get the following output.
```
hjorten@hjorten-1015PEM:~$ lspci | egrep -i --color 'network|ethernet'
01:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```

Which tells me that I have a Broadcom Corporation BCM4313 802.11bgn for the wireless.
What confuses me here, is that this one shouldn't support 5 GHz, but when using iwlist I get the following output.
Which seems to say that it has 5 GHz, but I'm not able to find any 5 GHz networks when checking for them.
Anyone who might know why this happens? Is it a wrong driver or setup at my Asus or?

```
hjorten@hjorten-1015PEM:~$ iwlist wlan0 freq
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.412 GHz (Channel 1)
```

---

