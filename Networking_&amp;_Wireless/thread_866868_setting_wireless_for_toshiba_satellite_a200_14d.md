---
title: "setting wireless for toshiba satellite a200 14d"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by maja_88 on 2008-07-22
Hi everyone. I am trying for so long to get my wireless working, and my greatest desire was to fix it myself but eventually I gave up. The thing is, I am at the moment very confused and I don't know what to do. Here is what I have:

I am using Ubuntu 7.10, kernel 2.6.22-14 generic
Wireless hardware: Intel PRO/Wireless 4965 AG(N); 
driver for it: driver: iwl4965

Now, I found a link which said that ubuntu 7.10 includes this driver and no installation is required, but in the wireless drivers window I see no driver installed. Then I followed the instructions at [http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi), I downloaded the driver, but apparently I don't have I don't have mac80211 subsystem installed and also
ls /lib/modules/$(uname -r)/build/Makefile shows that Makefile doesn't exist.

I really don't know what should I do..

Ah, one more thing: in the network-admin tab there is the wireless network detected, but it doesn't work. Does its being detected means that the driver is active indeed but the problem is in the newtork configuration?

I know this is very tiring to read.. I am sorry... I really hope that someone can help me..

---

### Post by sputnikkk on 2008-07-22
What are you trying to connect to?

Does the wireles router/AP use any version of encryption for security like WPA / WEP or WPA2?

I was having issues as are many many others with the default Netowrk Manager GUI that installed with Ubuntu 8.04 Hardy Heron.  I struggled for over a week trying to find a solution to getting my WORKING wireless settings to last thru a reboot.

[www.wicd.net](www.wicd.net)

[http://www.wicd.net/wiki/doku.php?id=faq](http://www.wicd.net/wiki/doku.php?id=faq)

Installed it - went in and configured my card in the gui interface it provides.  Worked first time out of the shoot.

Scanned the wireless AP's within range and told me their SSID's, I configured the settings for mine, and away it went.


Wicd - FTW.

All the best,

Sputnikkk

---

### Post by maja_88 on 2008-07-22
I have access to two wireless networks, one has WEP security the other one is unsecured. In windows both are detected and I but in ubuntu only the first one. However, as I mentioned it is not working.

---

### Post by sputnikkk on 2008-07-22
> Does its being detected means that the driver is active indeed but the problem is in the newtork configuration?

I suspect so ...

what happens when you do this at the command line in terminal:

```
lshw -C network
```

Post the output - lets see what the system sees as the cards

---

