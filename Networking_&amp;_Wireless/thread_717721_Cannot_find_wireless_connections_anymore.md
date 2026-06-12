---
title: "Cannot find wireless connections anymore"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by mrmoney on 2008-03-07
Hi guys,

for the longest time I was unable to get my wireless card working. That is until yesterday at which point I installed wpasupplicant and my wireless card was able to detect the wireless network at my home.

But, after rebooting my laptop I can no longer detect anymore wireless networks. iwlist scan produces no results.

Any idea what I need to do? As I said, it worked correctly immediatly after installing wpasupplicant, but upon reboot I can no longer detect the network.

here is the output of iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

thanks for any help. Sorry is this is an easy one, but I have searched and read the docs, and tried many things and I cannot get the network to be detected.

---

