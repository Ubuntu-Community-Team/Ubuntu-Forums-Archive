---
title: "Dell Inspiron 3542 Fn+Fx Wireless Switch not working."
date: 2014-07-26
forum: Networking &amp; Wireless
---

### Post by Lucky_Agarwal on 2014-07-26
Hi,

I recently purchased a Dell Inspiron 3542 Laptop with Ubuntu 12.04 pre-installed. Everything worked fine then.

Once I installed Ubuntu 14.04 on it the Fn+Fx combination for wireless on/off switch has stopped working.

I have attached wireless info tgz.

Please help me out.

Thanks in advance.

---

### Post by jeremy31 on 2014-07-26
Can you post the results of ```
lsmod
```

---

### Post by praseodym on 2014-07-27
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]16 dBm[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
Hi, the card is "on". Please check "lsmod"

---

