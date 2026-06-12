---
title: "High invalid misc on ath9k - is it a problem?"
date: 2017-06-20
forum: Networking &amp; Wireless
---

### Post by Oby on 2017-06-20
This may be an issue with a rather obvious answer, but my google-fu has not provided me with an answer. I therefore humbly ask for some help.

**Wifi information:** [http://paste.ubuntu.com/24909953/](http://paste.ubuntu.com/24909953/)

**My issue is that iwconfig shows a rather high "invalid misc" number. **

Here is an example from just a minute after connecting to the wireless network:
```
oby@ObyDesktop:~$ iwconfig
wlan0     IEEE 802.11  ESSID:"Oby"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: (hidden MAC)
          Bit Rate=195 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:56   Missed beacon:0

```

This increases steadily, but much more slowly, over time. Here is the same session, about 10-15 minutes later:
```
oby@ObyDesktop:~$ iwconfig
wlan0     IEEE 802.11  ESSID:"Oby"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: (hidden MAC)
          Bit Rate=195 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:191   Missed beacon:0

```

Notice that now I also have a handful of "Tx excessive retries".

My question is simply: is this indicative of a problem that I should be worried about? Or is it normal behavior? If it should worry me: how can I go about troubleshooting?

---

### Post by chili555 on 2017-06-20
> Or is it normal behavior?I think it's normal. My readings, for comparison:```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:2B:B0:DC:45:xx
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0 [COLOR="#FF0000"] Invalid misc:171 [/COLOR]  Missed beacon:0


```If your wireless is working as expected, I'd ignore it and enjoy Ubuntu.

[https://unix.stackexchange.com/questions/337488/wifi-too-much-invalid-misc-how-to-fix-it](https://unix.stackexchange.com/questions/337488/wifi-too-much-invalid-misc-how-to-fix-it)> That looks like a typical wifi interference problem. Try to locate the device causing the issue and when you do, delete this question as it would be off-topic. Simply turning most electronic equipment off and paying attention to what changes when the problems start can usually solve 90% of these.

---

