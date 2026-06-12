---
title: "wireless internet speed: live wifislax vs ubuntu 16.10"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by thosecars822 on 2016-11-26
Hello

I have a live wifislax in a pen drive.  Booting with it makes the wireless internet connection much faster than booting the same machine with the Ubuntu 16.10 installed in the machine's hard drive. It is a weird behaviour and I do not know why that might happen. What i mean is that websites get opened much quicker with the live wifislax than with ubuntu 16.10 for some strange reason. Another example: Internet videos get streamed in the live wifislax distribution without lag but the lag in Ubuntu is extremely annoying.

Does anyone have any idea how to fix this in Ubuntu 16.10? The speed diference is really noticeable.


Thanks

---

### Post by wildmanne39 on 2016-11-26
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by thosecars822 on 2016-11-26
I'm gonna do what you suggested and I wil post the output afterwards.  Anyway I just noticed another thing: the fan is also at maximum speed  all the time with Ubuntu, whereas the fan is quite quiet in general with  the live Wifislax.

---

### Post by wildmanne39 on 2016-11-26
> Anyway I just noticed another thing: the fan is also at maximum speed all the time with Ubuntu, whereas the fan is quite quiet in general with the live Wifislax. You need to start a new thread in the appropriate section of the forum with a descriptive title for this issue, we only allow one topic per thread!
Thanks

---

### Post by thosecars822 on 2016-11-27
Hello again

Please find the file "wireless-info.tar.gz" attached.

Thanks

---

### Post by wildmanne39 on 2016-11-27
Did you upgrade from a previous version of Ubuntu because your wifi is named wlan0 and it should not be in 16.10 unless you upgraded or set it that way by modifying configuration files?

Set your wireless settings in network manager in the top right corner of the screen to match the screenshots below.

Check the settings in the router your WPA2-AES is the best not WPA and WPA2 mixed mode and certainly not TKIP.
save and reboot the router.

Yours looks like it is set to wep that is out dated and not secure.

Your country code is set to 00 which is basically a generic setting for the U.S. so if you are in Madrid like it says you need to change setting by do:
```
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
```If Madrid is not where you are then use the link to find your code and substitute your code for the ES in the command above.
[https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) 
Reboot computer, and we may have to set a static Mac Address because of all the networks around you.

---

