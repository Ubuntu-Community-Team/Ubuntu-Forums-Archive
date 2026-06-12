---
title: "ZyAir B-100 (prism) won't connect"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by flaxx on 2008-01-17
Hello everybody

I am what you might consider a linux 'noob', but as a systems administrator I'm quite used to the Windows world and computer systems in general.

I run Xubuntu 7.04 on an old Compaq Armada M300 notebook with a ZyAir B-100 PCMCIA 802.11b WLAN card, but I can't connect to any networks. No matter if I use WPA, WEP or no encryption at all, it just won't connect - that is, the network icon in XFCE turns into some animated circle and then back into two "not connected" computers. I can't connect to any network, be it at home (a WRT54G, if this is of interest), at work or at university - so it's certainly not an access-point or configuration-related problem.

The card's "power" LED is constantly on while "link" is blinking. This card has a Prism3 chipset which should be supported in current ubuntu, so I've read and done the steps of [this article.](http://linux.junsun.net/intersil-prism/) Other WLAN cards which I tried worked fine, so it's not a PCMCIA problem or something.

hostag_diag wlan0 returns
```
Host AP driver diagnostics information for 'wlan0'

NICID: id=0x801b v1.0.0 (PRISM III PCMCIA (SST parallel flash))
PRIID: id=0x0015 v1.1.1
STAID: id=0x001f v1.7.4 (station firmware)
```


iwconfig returns the following:
```

wifi0     IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

Personally I suspect that the transpit power of the card is set too low, any way to change this? Any other suggestions?

And yeah, if I boot with the card plugged in, xubuntu won't start / screen remains black. But that's probably another problem.

Thanks in advance for any suggestions

---

