---
title: "Ubuntu 13.04 Networking issue"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by A_Sastry on 2013-09-11
I recently installed Ubuntu 13.04 on my Dell Vostro 1500 laptop and this is my first time I am trying to use Ubuntu. 
Looks like the system is not detecting any networks, that is both wireless networks including the one at my home and the wired network. 
I was able to connect to my home wifi on other devices without any problem. Tried to explore different settings and didn't succeed. 

I see the network controller as BCM4311 802.11a/b/g and the Ethernet controller as BCM4401-B0. Do I need to install any drives for them ?
Any clues ?

Thanks.

---

### Post by chili555 on 2013-09-11
Please hook up the ethernet temporarily, open a terminal and do:```
sudo modprobe b44
```Now your ethernet should be working. Next do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and enjoy.

---

### Post by A_Sastry on 2013-09-12
Thanks so much. The first code did not respond or did nothing. It was just clocking and I had to kill it after several minutes.

Out of second set of codes (for wireless) the first code executed fine. But the next one failed saying the package not found. So, I downloaded the package linux-firmware-nonfree and trying to install the package. But getting into some obstacles. Can you direct me with some more instructions ? Thanks again.

---

### Post by chili555 on 2013-09-12
I assume you downloaded a .deb file. Assuming it is on your desktop, open a terminal and install it with:```
sudo dpkg -i Desktop/linux-firm*.deb
```Note any errors and post here.> The first code did not respond or did nothing. It was just clocking and I had to kill it after several minutes.Let's see the message log about this:```
dmesg | grep b44
```

---

### Post by A_Sastry on 2013-09-13
Yes, thats the .deb file. So, I used your code to install the .deb file (linux-firmware-nonfree). It was installed successfully.
After restarting my laptop the wired network starting functioning now. But still no luck with the wireless connections. Its still not reading any wifi networks around.

Thanks for helping with this.

---

### Post by chili555 on 2013-09-13
Let's check the message logs.```
dmesg | grep -e b43 -e wlan
```

---

### Post by A_Sastry on 2013-09-17
Sorry for responding little late. But, here is what happened in the mean time. I repeated the two steps you mentioned earlier. 

[I]sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree 

[/I]Now, I can see the wireless networks now and was able to connect without any probs. 
Bascially, those two steps resolved my network issue. I really appreciate your support. Thanks.

---

