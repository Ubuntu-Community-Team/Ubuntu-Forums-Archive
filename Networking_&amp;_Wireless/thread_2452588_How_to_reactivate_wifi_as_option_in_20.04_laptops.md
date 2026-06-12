---
title: "How to reactivate wifi as option in 20.04 laptops"
date: 2020-10-25
forum: Networking &amp; Wireless
---

### Post by wmrp on 2020-10-25
2 laptops in the household running Ubuntu 20.04 are set up to work as wired (ethernet) devices. They are therefore in airplane mode by default. When on the road wifi cannot be turned on, because it says to use hardware switch to turn off airplane mode. What is a hardware switch? 
Devices in question: 
Toshiba Satellite C875
Dell Latitude E7470

I suspect that this may be the wrong place to ask this, and I should consult a manual for the respective devices. Just not sure if this is a Ubuntu thing or not.

---

### Post by kc1di on 2020-10-25
On each one you'll have a combination of F Keys that turn wifi on and off. 
On mine (Lenovo) it's the F8 key But if you do an on line search for each model you should be able to find the key combo on your machines that turn it on.
Some dells have a actual switch on the side of the machine.  Others use F keys. Good Luck.

Also depending upon the wifi card chip set in each you may have to install additional drivers.

---

### Post by cmcanulty on 2020-10-25
I have had that happen. If I have trouble getting the wifi, I turn it off with whatever key does it, wait a few seconds and turn the wifi key back on. Presto it picks up the wifi.Works every time.

---

### Post by wmrp on 2020-12-09
It is stuck on airplane mode, that is why wifi is unavailable. The F keys don't change anything there. And so-called hardware switch is nowhere to be found (not mentioned in user manual either). Might a complete reinstall of 20.04 do the trick?

---

### Post by cmcanulty on 2020-12-09
Try this fix just copy and paste commands so they are acurate.

[https://itsfoss.com/restart-network-ubuntu/]("https://itsfoss.com/restart-network-ubuntu/")

---

### Post by wmrp on 2021-01-03
> **cmcanulty said:**
> Try this fix just copy and paste commands so they are acurate.

[https://itsfoss.com/restart-network-ubuntu/](https://itsfoss.com/restart-network-ubuntu/)

Reading the article gave me hope, but unfortunately none of the methods did anything.

---

### Post by chili555 on 2021-01-03
>  And so-called hardware switch is nowhere to be found (not mentioned in user manual either).Please see: [https://supportkb.dell.com/img/ka02R000000hDKqQAM/ka02R000000hDKqQAM_en_US_1.jpeg](https://supportkb.dell.com/img/ka02R000000hDKqQAM/ka02R000000hDKqQAM_en_US_1.jpeg)

Doesn't the PrtScr key have a wireless symbol on it?

Please run in the terminal:

```
rfkill list all
```

Note the result. We suspect it says HardBlocked:Yes. Press the PrtScr key and then run again:

```
rfkill list all.
```

Does the result change? Is your wireless now working?

---

### Post by #&amp;thj^% on 2021-01-03
Ha  Ninja'd by chili :P
See the output of "rfkill" to determine if yours is a Software or Hardware lock.
```
>> rfkill
ID TYPE      DEVICE                   SOFT      HARD
 0 bluetooth tpacpi_bluetooth_sw unblocked unblocked
 1 bluetooth hci0                unblocked unblocked
 2 wlan      phy0                unblocked unblocked

```

---

