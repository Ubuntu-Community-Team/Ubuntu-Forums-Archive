---
title: "AR5007EG almost set up.."
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by BenRain on 2007-12-24
I have installed the device sucessfully apparantly in ndiswrapper and am using wicd. I just need help with the final steps

ben@ben-laptop:~/802ABG_atheros_v4.2.2.7$ sudo ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
ben@ben-laptop:~/802ABG_atheros_v4.2.2.7$ 

Is what is listed in the Terminal client. 

In the Wicd config I have  the wired interface set as eth0 and I can't figure out what to set the wireless interface to. I've tried wlan1 and 0 but no luck, any tips or advice?

Also with lspci my card displays as an Atheros 5006EG instead of a 7.

---

### Post by chalewa on 2007-12-24
> **BenRain said:**
> I have installed the device sucessfully apparantly in ndiswrapper and am using wicd. I just need help with the final steps

ben@ben-laptop:~/802ABG_atheros_v4.2.2.7$ sudo ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
ben@ben-laptop:~/802ABG_atheros_v4.2.2.7$ 

Is what is listed in the Terminal client. 

In the Wicd config I have  the wired interface set as eth0 and I can't figure out what to set the wireless interface to. I've tried wlan1 and 0 but no luck, any tips or advice?

Also with lspci my card displays as an Atheros 5006EG instead of a 7.

post the output of 

```
ifconfig
```

---

### Post by BenRain on 2007-12-25
Okay, I got my wireless card working! Horray! just a slight problem.

All the network managers I've tried won't save my login information or automatically connect, so I find myself typing
```

sudo iwconfig wlan0 essid SSID-Here key WEP-Key-Here
sudo dhclient wlan0

```
every time I start up.


Is there a way to make a windows-like batch file to prevent from typing this in?

---

### Post by FastZ on 2007-12-26
run these commands...

```

gedit autoconnect

```

then type the following

```

#!/bin/bash
sudo iwconfig wlan0 essid SSID-Here key WEP-Key-Here
sudo dhclient wlan0

```

then 

```

chmod +x autoconnect

```

then from now on, all you have to do is run ./autoconnect from the directory the autoconnect script is located and type your sudo password whenever prompted to do so.

---

### Post by icaris13 on 2007-12-30
> **BenRain said:**
> I have installed the device sucessfully apparantly in ndiswrapper and am using wicd. I just need help with the final steps

ben@ben-laptop:~/802ABG_atheros_v4.2.2.7$ sudo ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
ben@ben-laptop:~/802ABG_atheros_v4.2.2.7$ 

Is what is listed in the Terminal client. 

In the Wicd config I have  the wired interface set as eth0 and I can't figure out what to set the wireless interface to. I've tried wlan1 and 0 but no luck, any tips or advice?

Also with lspci my card displays as an Atheros 5006EG instead of a 7.

BenRain, 
  I have the same wireless card and when I type sudo ndiswrapper -l I get the same output you posted above.  You said in a later post that you got wifi working,  What did you do?  I installed the correct driver using ndiswrapper and blacklisted the others, but am at a standstill now, any help?

---

