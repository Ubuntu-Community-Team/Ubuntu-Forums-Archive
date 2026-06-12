---
title: "find out module version"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by cccc on 2006-09-07
hi

I have dapper drake

howto find out the exact version of the module installed on my system, 
for example of the network card ?

kind regards
cccc

---

### Post by souki on 2006-09-07
first, you need to know the name of the module with something like that:
```
dmesg | grep eth0
``` then you can use this command :
```
modinfo module-name
```

---

### Post by cccc on 2006-09-07
> **souki said:**
> first, you need to know the name of the module with something like that:
```
dmesg | grep eth0
``` 
thanks, but```

# dmesg | grep ath0
[17179592.560000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179592.560000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179592.560000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179592.560000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179592.560000] ath0: mac 7.9 phy 4.5 radio 5.6
[17179592.560000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179592.560000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179592.560000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179592.560000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179592.560000] ath0: Use hw queue 8 for CAB traffic
[17179592.560000] ath0: Use hw queue 9 for beacons
[17179592.560000] ath0: Atheros 5212: mem=0xdff90000, irq=11
[17179619.116000] ath0: no IPv6 routers present

```
cannot see the module

---

### Post by cccc on 2006-09-07
why this forum is so extremely slowly ?

---

### Post by souki on 2006-09-08
the module name should be "ath_pci"

---

### Post by cccc on 2006-09-08
> **souki said:**
> the module name should be "ath_pci"

I know that ! 

I need to know the version of the madwifi driver installed on my system.

---

### Post by souki on 2006-09-11
I don't understand, what gives you 'modinfo ath_pci' ?

---

### Post by tbonius on 2006-09-11
First off.. Souki is trying to help you.  He is correct in asking the version returned by "modinfo".  

Secondly, the madwifi driver set for your kernel loads a module called ath_pci (or whatever other modules are required).

Check "lsmod" to find the loaded modules.

```
lsmod |grep ath
```

Any modules that are loaded we can get info out of by running the "modinfo" command.  You can check the major and minor versions against the kernel source and determine the version of the drivers themselves against the version of the kernel source.

T

---

