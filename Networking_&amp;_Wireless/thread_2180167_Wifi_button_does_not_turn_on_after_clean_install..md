---
title: "Wifi button does not turn on after clean install."
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by unixpcguy on 2013-10-11
Hi everyone):P; I'm fairly new here. I been messing around with Ubuntu 10.10 lately. I just ran a clean install on my HP DV5 Pavilion notebook. I know the Wi-Fi works because it works on my Win 7 Ultimate setup (which is also installed on the same unit). Does anyone know the code to activate it via terminal? I think it is "hard blocked" as it's called. Any help would be appreciated.

---

### Post by praseodym on 2013-10-11
Hi,

Ubuntu 10.10 is outdated. I strongly recommend installing 12.04 long term support (LTS). For 10.10: Try to reset the BIOS to default settings.

---

### Post by unixpcguy on 2013-10-11
Thanks praseodym :)

---

### Post by grahammechanical on 2013-10-12
The wireless adapter may be working but is it recognised by Ubuntu? In other words does Ubuntu have a driver for it? Is it switched on in Ubuntu? It is years since I did anything on Ubuntu 10.10 and at that time I did not know what I was doing. Run this command

```
rfkill list
```

If it says soft blocked: yes, then the adapter is not switched on in software. How you do that with Network Manager in 10.10 I cannot say. If it says hard blocked:yes then the adapter is switched off by some hardware switch. Perhaps a keyboard combination.

Also I have heard that if we switch off wireless in Windows then wireless will not be activated in Ubuntu. And Ubuntu cannot switch it on. Try running

```
sudo ifconfig wlan0 down
```

followed by

```
sudo ifconfig wlan0 up
```

Regards.

---

### Post by unixpcguy on 2013-10-25
Solved it; I just installed a clean copy of 13.10 64 bit. It works fine. Thanks all :) . It may have been that it was out of date.

---

