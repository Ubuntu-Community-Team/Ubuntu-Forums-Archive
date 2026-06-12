---
title: "Weird ath9k bug rabbit hole."
date: 2020-10-06
forum: Networking &amp; Wireless
---

### Post by christophu on 2020-10-06
This is a rabbit hole of a bug I've found myself experiencing for the first time despite using the same card on linux for years until I did a fresh 20.04 install. Here are some relevant logs.

dmesg displays two types of messages I believe are related to the issue.

```
[  350.557566] wlo1: authenticate with 10:c3:7b:ce:7e:ac
[  350.572826] wlo1: send auth to 10:c3:7b:ce:7e:ac (try 1/3)
[  350.573878] wlo1: authenticated
[  350.576777] wlo1: associate with 10:c3:7b:ce:7e:ac (try 1/3)
[  350.578061] wlo1: RX AssocResp from 10:c3:7b:ce:7e:ac (capab=0x11 status=0 aid=4)
[  350.578201] wlo1: associated
[  680.361521] ath9k 0000:21:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xfdee1544 flags=0x0000]
[  680.425700] ath9k 0000:21:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xfe720fc4 flags=0x0000]
[  680.425707] ath9k 0000:21:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xfe721000 flags=0x0000]
[  680.489520] ath9k 0000:21:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xff0d5a44 flags=0x0000]
[  680.650051] wlo1: authenticate with 10:c3:7b:ce:7e:ac
[  680.665173] wlo1: send auth to 10:c3:7b:ce:7e:ac (try 1/3)
[  680.666229] wlo1: authenticated
[  680.669072] wlo1: associate with 10:c3:7b:ce:7e:ac (try 1/3)
[  680.670356] wlo1: RX AssocResp from 10:c3:7b:ce:7e:ac (capab=0x11 status=0 aid=4)
[  680.670494] wlo1: associated
```

[  680.361521] ath9k 0000:21:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xfdee1544 flags=0x0000] I have found to be related to IOMMU issues from looking around, but I couldn't find a fix directly related to ath9k reporting this error. The rest of the errors are what I generally see every minute or less, caused by the dropping and re-authing to the network. 

iwconfig doesn't show anything off the top of my head that would fix this problem.

```
enp34s0   no wireless extensions.

virbr0    no wireless extensions.

wlo1      IEEE 802.11  ESSID:"MoonlightYuh"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: 10:C3:7B:CE:7E:AC   
          Bit Rate=270 Mb/s   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:173   Missed beacon:0

virbr0-nic  no wireless extensions.

lo        no wireless extensions.

```

I've tried setting options ath9k nohwcrypt=1 in the ath9k config with no success, I've also seen that this could be related to numerous things, such as a broken / buggy wpa_supplicant, band / channel settings on my router (all other devices work fine, same card connects fine under different OS). I'm struggling to find anything to fix this bug and have even bumped a years old thread with a similar issue on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/495981").

[https://pastebin.com/T2rZq6B3](https://pastebin.com/T2rZq6B3) contains the entire wifi troubleshooting script output.

---

### Post by chili555 on 2020-10-08
> band / channel settings on my router (all other devices work fine, same card connects fine under different OS).I suspect that is at least partially and maybe completely the issue.

<rant>
A great many things work perfectly in That Other O/S but not in Ubuntu and vice versa. We can steadfastly refuse to make any accomodation or we can make a slight change,connect and be happy.

Linux will, indeed, always have driver issues, but for several reasons that may not be apparent to all of us. First, new devices are developed and released every day. The manufacturers are in a constant arms race to have a better device with more features and, often, cheaper. In almost every case, they have little or no concern for the 1-2% of Linux users and therefor don't provide a working driver.

In cases where the manufacturer provides a driver, then they are the ones to blame for its flaws. 

Note the author of your driver:

```
$ modinfo ath9k
filename:       /lib/modules/5.4.0-48-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
[COLOR="#FF0000"]author:         Atheros Communications[/COLOR]
```
</rant>

When you posted your question, we see:> wlo1      IEEE 802.11  ESSID:"MoonlightYuh"  
          Mode:Managed  [COLOR="#FF0000"]Frequency:5.2 GHz [/COLOR] Access Point: 10:C3:7B:CE:7E:AC   
          Bit Rate=270 Mb/s   Tx-Power=18 dBm   
          <snip>

When you ran the wireless script, we see:> 
MoonlightYuh                    <MAC 'MoonlightYuh' [AN14]>  Infra  153  [COLOR="#FF0000"] 5765 MHz[/COLOR]  405 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2      
Your router is, once your wireless is connected, switching channels, always looking for a better connection, just like my ex-girlfriend.

I suggest that you change the channel in the router to a fixed channel rather than auto-select. 

Is there any improvement?

---

