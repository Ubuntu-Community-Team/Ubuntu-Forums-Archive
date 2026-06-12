---
title: "New Router with 5 Ghz and 4.2 Ghz. Can oly see 4.2 on main laptop"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by irv on 2017-07-19
I just purchased a Kasda AC1200 Dual Band Gigabit Wireless Router, Long Range WiFi Router 5dBi High Gain Antenna, Gigabit Ports Router, Easy Setup Via Cellphone, USB3.0, Dual Core Processor Based (AC1200 Link Smart / KW6516). It was an easy setup and is working fine, but I have one issue.
It comes with a 5Ghz and a 2.4Ghz which can be setup as two different connections. I set it up this way. When I go on my wife's Chromebook and my small Dell laptop running Ubuntu Gnome, I can see the 5G and the 2.4G networks. But when I go on my Asus (main laptop) I can only see the 2.4G network. I am running Ubuntu Gnome on it as well. Now I have Windows 10 installed on it, so when I go into Windows, I have the same issue. Only the 2.4G shows up. So I don't think it is an OS issue but some setting on the hardware. I went into the BIOS, but I can't find a setting that would not allow me to see a 5Ghz connection.
Does anyone have any idea what is going on. Is it possible that my hardware does not support 5Ghz. My main laptop is much newer than the Dell, so I am not sure why it won't see the 5G.
My little slow Dell is running at 50 Mbps down load at the 5G, where my faster laptop is only running at 30 Mbps at the 2.4G. This is all on the wireless. Compared to my old router this one is running much faster, but this 5G is got me puzzled, why I can see it on my main laptop.

---

### Post by irv on 2017-07-19
Does this mean my wifi card does not support 5 Mhz?
```
irv@irv-Q500A:~$ iwconfig
enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"irv-network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0E:F4:ED:BE:73   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:10204   Missed beacon:0

lo        no wireless extensions.

irv@irv-Q500A:~$ iwlist wlp2s0 freq
wlp2s0    13 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)

```

---

### Post by irv on 2017-07-19
I found that my Intel Centrino wireless N2230 wifi card does not support 5 Mhz.
> The Intel(R) Centrino(R) Wireless-N 2230 is a single band adapter and works on the 2.4GHz band ONLY. It does have Bluetooth.
I will mark this as solved.

---

