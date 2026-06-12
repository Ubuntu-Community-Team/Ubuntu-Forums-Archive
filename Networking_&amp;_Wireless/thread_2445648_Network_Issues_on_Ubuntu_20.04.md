---
title: "Network Issues on Ubuntu 20.04"
date: 2020-06-17
forum: Networking &amp; Wireless
---

### Post by leflea on 2020-06-17
Hey guys, sorry I feel like this question is super simple but I JUST installed Ubuntu from a USB and did not see any way to connect to the internet in the hotbar. When I went in the network setting the only ones available were just to setup a VPN, I can't find any wireless connections, and I do not own an ethernet cable to try a wired connection.

I tried searching the internet for help, but all of it was outdated, and did not work for me.

Thank you so much for the help!

---

### Post by CelticWarrior on 2020-06-17
Welcome.

Is it a laptop? If so you can check your networking hardware with ```
lspci -knn | grep Net -A3
``` and then post the result here, preferably in code tags (Go advanced, press "#" and paste inside).
This should be enough to know what to do.

---

### Post by leflea on 2020-06-17
Sorry, I don't know how to go advanced in the terminal, so I'll just post what it said when I typed that in

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
             Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b.0117]
             Kernel driver in use: bcma-pci-bridge
             Kernel modules: bcma
04:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SS9183 PCIe SSD Controller [1b4b:9183] (rev 14)


Also I'm accessing the forum from a separate computer and just had to type all that out, do you know of an easier way because that might take a while if this goes on

---

### Post by CelticWarrior on 2020-06-17
It's not "go advanced" in terminal, it's the "Go Adavanced" button right here when posting. It opens a lot more formatting options including the one I mentioned. ;-)
Also there's a specific "Networking & Wireless" section in the forum. That section is more appropriated for your question and there you would find this sticky thread [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) which is all about Broadcom chipsets like the one you have.

So, from there, we can find that the driver installed automatically is likely wrong. Remove and install the correct one. You need an alternative internet connection. We know you don't have an Ethernet cable. You can use USB tethering from your phone (it'll take seconds and the data to download is negligible):

```
sudo apt remove bcma-pci-bridge
sudo apt install bcmwl-kernel-source
```

Reboot and the WiFi should be working.

---

### Post by leflea on 2020-06-17
First of all, I wanted to thank you so much for being so kind and helpful, I really appreciate it

I turned the hotspot on my phone on, and connected it to my computer, and everything was fine with that

I typed in "sudo apt remove bcma-pci-bridge" and it keeps repeating "Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend It is held by process 2296 (apt)" and then there is a timer in seconds after it

---

### Post by CelticWarrior on 2020-06-18
That message appears whenever another process is accessing the database. Usually the system is checking for/trying to install updates in the background. This may happen with or without internet connection. Just wait a couple of minutes an try again.

---

### Post by slickymaster on 2020-06-18
*Thread moved to **Networking & Wireless**.*

---

