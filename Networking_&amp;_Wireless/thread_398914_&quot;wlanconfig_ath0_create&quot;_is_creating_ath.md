---
title: "&quot;wlanconfig ath0 create&quot; is creating ath1 instead of ath0"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by dr_d12 on 2007-04-01
I'm hoping to get some help with monitor mode. I can switch between monitor mode, managed or master with wlanconfig, but when I create ath0 with monitor mode, it says ath0, but actually ends up as ath1 under iwconfig instead of ath0. Why?? It doesn't seem to matter how I take down or destroy ath0, I can't make a monitor mode ath0. Am I missing something here?
Thanks,
Dave

```

~$ sudo wlanconfig ath0 destroy
~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed
ath0
~$ iwconfig
ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.23 GHz  Access Point: Not-Associated   
               (cut)

~$ sudo wlanconfig ath0 destroy
~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ath0
~$ iwconfig
ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Channel:0  Access Point: Not-Associated   
               (cut)


~$ sudo wlanconfig ath1 destroy
~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode master
ath0
~$ iwconfig
ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Master  Frequency:5.805 GHz  Access Point: Not-Associated   
               (cut)


```

---

### Post by Sivar on 2008-01-14
I filed a bug report with solution. See bug# 182988

--Charles Burns

---

