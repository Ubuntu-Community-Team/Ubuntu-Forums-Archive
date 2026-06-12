---
title: "Lost eth1 IPW2200"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by Neondog82 on 2007-09-25
Hello everyone, yet again I need some help. I recently installed Aircrack-ng on my laptop. i successfully applied the patch and all was working well. Then suddenly every time I tried to connect to my AP the computer locked up. Some how in the process I lost my eth1.

I have tried everything mentioned else where and nothing is working.

I completely removed ieee80211 and installed V2.18 and V2.17
Also I tried to reinstall IPW2200 V.1.2.1
Lastly I tried to install the IPW firmware by transferring the files to these directories:
     -/lib/firmware/2.6.20-15-generic
     -/lib/firmware/2.6.20-16-generic
     -/lib/firmware/ipw2200-fw-3.0

---

### Post by Neondog82 on 2007-09-25
this is what i got so far:

lspci shows my Intel Pro Wireless 2200BG 

iwconfig and ifconfig does not show eth1

sudo modprobe ipw2200 kicks out an error and says to view dmes

dmesg states ipw2200: Unknown parameter 'rtap_iface'

Could the above help anyone help me on my way?

---

### Post by Neondog82 on 2007-09-25
well I managed to get my eth1 back. I was searching the web for the dmesg i got. I saw iin one of the google searches the words "insmod ipw2200.ko" so i typed in and bam, it pops up asking me for the key to my wireless network. However it is important to not that I manually deleted the ipw2200.ko file from the /lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless directory. Then I replaced it with the ipw2200.ko file I manually compiled from the ipw2200-1.2.1 folder I download from Source Forge.

---

### Post by Neondog82 on 2007-09-25
Ok, that worked untill I restarted the computer. Any further ideas?

---

### Post by Neondog82 on 2007-09-26
Again, i made some more progress but still need help.

Every time I restart my computer I have to re install the ipw2200-1.2.1. drivers, and then give the command "sudo insmod ipw2200.ko"

Also I recieved this message with the following commands? What is that first error?

```
neondog82@Linux:~/aircrack/Driver/ipw2200-1.2.1$ dmesg | grep ipw2200
[   35.468000] ipw2200: Unknown parameter `rtap_iface'
[  318.304000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1
[  318.304000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  318.304000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  318.640000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
neondog82@Linux:~/aircrack/Driver/ipw2200-1.2.1$ dmesg | grep ieee80211
[   35.356000] ieee80211_crypt: registered algorithm 'NULL'
[   35.408000] ieee80211: 802.11 data/management/control stack, 1.2.17
[   35.408000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  349.712000] ieee80211_crypt: registered algorithm 'CCMP'
neondog82@Linux:~/aircrack/Driver/ipw2200-1.2.1$ 
```

---

