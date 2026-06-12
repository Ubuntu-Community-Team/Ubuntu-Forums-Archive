---
title: "Using my ubuntu laptop slows down connection for all devices"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by joakim4 on 2015-01-10
Hi

I have a weird problem that I have no idea how to solve or even localize. When I use my laptop internet slows down enormously, (ping [www.google.com](www.google.com) goes from 20ms to >2000ms). It doesn't happen immediately but invariably it sets in after a while,
sometimes (seldom) it's solved by disconnecting and reconnecting. I have tried on two different home networks (with different routers and ISP's) and it happens on both. However, it doesn't happen at work. It doesn't matter if I use wireless or cable connection.

Now the weird part, it doesn't only affect my laptop but all devices connected to the network. This, combined with the fact that it doesn't happen at work where I probably have less permissions, leads me to think that my laptop somehow "drowns" the router.

I have quite limited knowledge about networking and I don't know how to diagnose this further so any advice or suggestions as to what the problem might be will be much appreciated :)

INFO:

Lenovo ThinkPad T440p
Ubuntu 12.04

---

### Post by chili555 on 2015-01-10
We have heard of this syndrome before and, in fact, solved it yesterday. Before we proceed, please identify your wireless device. Open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e wl -e brcm
```Thanks.

---

### Post by wildmanne39 on 2015-01-10
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by joakim4 on 2015-01-10
Thanks, I attached the output from the script.

---

### Post by chili555 on 2015-01-10
> **joakim4 said:**
> Thanks, I attached the output from the script.Take it, Wild Man!

WEP you say? WEP??

---

### Post by joakim4 on 2015-01-10
> **chili555 said:**
> Take it, Wild Man!

WEP you say? WEP??

Should I not have posted all of it? The instructions said private information was removed.

---

### Post by chili555 on 2015-01-10
It's not that at all. Wild Man and I are horrified that the network is encrypted with WEP.> *NUMERICABLE-E2B4: Infra, <MAC 'NUMERICABLE-E2B4' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 [COLOR="#FF0000"]WEP[/COLOR]It is about as secure as placing your money and credit cards in a shoebox on the front porch. It can easily be hacked in mere minutes. While we await Wild man, I strongly suggest you change the router's encryption to WPA2-AES.

[https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)> Depending on the amount of network traffic, and thus the number of packets available for inspection, a successful key recovery could take as little as one minute. 

---

### Post by joakim4 on 2015-01-10
Ah, I see, done :)

---

### Post by chili555 on 2015-01-10
Excellent! Does the slowdown persist? May we see another wireless script?

Wild Man is remarkably silent...

---

### Post by chili555 on 2015-01-10
Excellent! Did you reboot the router? Does the slowdown persist? May we see another wireless script?

Wild Man is remarkably silent...

---

### Post by wildmanne39 on 2015-01-10
Just got back from havig Birthday dinner with my family. You were here first so I wll just watch.

---

### Post by joakim4 on 2015-01-11
OK, here is a new script output. The slowdown hasn't set in yet, will see how the day goes.

---

### Post by joakim4 on 2015-01-11
Yep, the problem is still there.

---

### Post by chili555 on 2015-01-11
Let's try one more relatively easy step before we get out the big hammer!```
sudo ifconfig wlan0 down
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
sudo ifconfig wlan0 up
```Does it help? If so, make it persistent:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Do not undertake the echo step unless the first step helps.

---

### Post by joakim4 on 2015-01-11
I get an error message from the modprobe -r iwlfwifi command:
FATAL: Module iwlwifi is in use.

I manually disconnected from the network and tried but got the same result. Carrying out the four commands anyway did not help.

---

### Post by chili555 on 2015-01-11
If you got the same result, I'm sure the parameter didn't take. Let's try again:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us hear your report.

If all this is ineffective, then let's update the driver.```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic
```You may also need later firmware. Please download the iwlwifi-7260-22.24.8.0 firmware to your desktop: [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware) Right-click it and select 'Extract Here.' Now do:```
cd ~/Desktop/iwlwifi-7260-ucode-22.24.8.0
sudo cp iwlwifi-7260-8.ucode  /lib/firmware/
```Reboot and let us hear your report.

---

### Post by joakim4 on 2015-01-15
After a few days without any troubles it seems like the

```

sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

did the trick!

Thanks for the help.

---

