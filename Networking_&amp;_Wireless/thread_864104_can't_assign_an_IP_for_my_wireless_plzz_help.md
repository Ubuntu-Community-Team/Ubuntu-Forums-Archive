---
title: "can't assign an IP for my wireless: plzz help"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by NotSoInnocent on 2008-07-19
Hi

I recently installed ubuntu in my laptop, and I can't connect to the wireless network. I have an intel Pro/wireless 3945ABG card, and I know it is supported. The driver is supposed to be installed by default, but I couldn't find it even though I enabled the restricted repository. So I installed the .inf driver that I have for windows xp, and it seems to be working. At least now I can see my AP in the list.

This is the output of iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SpeedStream"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Fragment thr=35613 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


It is telling me the AP is not associated. I can't get an IP address, and when I try to connect, it shows that I am connected with a 0% signal strength, even though the actual signal strength is actually high.


The content of my /etc/network/interfaces  file is this:

auto lo
iface lo inet loopback



I tried adding an entry for wlan0 manually, but that didn't work. The AP is not encrypted. I tried connecting using the terminal instead of the network manager as shown in one of the tutorials here, but that didn't work either. When I use dhclient wlan0, it tells me there are no leases in persistent database. 

Does anyone know what the problem could possibly be?  :confused:

---

