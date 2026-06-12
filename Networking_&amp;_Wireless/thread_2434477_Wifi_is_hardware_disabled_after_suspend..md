---
title: "Wifi is hardware disabled after suspend."
date: 2020-01-06
forum: Networking &amp; Wireless
---

### Post by yathomasi on 2020-01-06
laptop is hp pavillion and wireless hardware is Intel Wireless 3165. The main problem is wifi is hardware disabled on suspend.
Tried secure boot off still same issue as below.
More details can be found here:
[https://paste.ubuntu.com/p/2mkxFvr54G/](https://paste.ubuntu.com/p/2mkxFvr54G/)

I had posted it on AskUbuntu and didn't got response check this out too
[https://askubuntu.com/questions/1197431/wifi-is-automatically-disabled-on-sleep-suspend-wifi-is-disabled-with-hardware/1197547#1197547](https://askubuntu.com/questions/1197431/wifi-is-automatically-disabled-on-sleep-suspend-wifi-is-disabled-with-hardware/1197547#1197547)

---

### Post by praseodym on 2020-01-06
Please show

```
lsmod
```

completely. What about
```

sudo rfkill unblock all
rfkill list
```

---

### Post by yathomasi on 2020-01-07
Thanks for the response @parseodym
Here is the result of the commands

[ATTACH]284759[/ATTACH]
[ATTACH]284758[/ATTACH]

---

### Post by CelticWarrior on 2020-01-07
*hard blocked: yes*

This means a physical switch (or a F key or key combo) to enabled/disable the WiFi. If it becomes disabled automatically when suspending, just use the proper switch to enable it again.

---

### Post by yathomasi on 2020-01-08
@CelticWarrior thanks for the reply
Sorry, there is no hardware switch. Should have explained in question
Just ariplane switch on f12 which works only when wifi is on and doesn't work after wifi is disabled by hardware.

Also,setting on closing the lid is ignore
HandleLidSwitch=ignore
So when I close the lid it closes wifi which can be enabled using airplane(f12) switch or ```
[COLOR=#000000][FONT=&amp]sudo rfkill unblock all[/FONT][/COLOR]
```

---

