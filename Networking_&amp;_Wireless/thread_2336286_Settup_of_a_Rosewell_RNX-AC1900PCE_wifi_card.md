---
title: "Settup of a Rosewell RNX-AC1900PCE wifi card"
date: 2016-09-06
forum: Networking &amp; Wireless
---

### Post by nanth on 2016-09-06
I just got a Rosewell RNX-AC1900PCE wifi card from amazon for my new desktop. I've looked with no success finding the necessary driver. Could anyone tell me the link to the driver with instructions on how to install it for Ubuntu 14.04? A couple of the reviews on it said it worked with Ubuntu so it should be possible to get it working.

Thank you in advance!

---

### Post by chili555 on 2016-09-06
Let's start by identifying the device. Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```Thanks.

---

### Post by nanth on 2016-09-07
It says

03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
          Subsystem: Broadcom Corporation Device [14e4:0619]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)

Thank you so much for your quick response!

---

### Post by chili555 on 2016-09-07
What is your kernel version?```
uname -r
```I am not sure it is even possible to get it going in 14.04. If you have an ethernet connection, you might try:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```If you have the installation USB or DVD, we can get the drivers there.

---

### Post by nanth on 2016-09-07
The kernel is 3.19.0-68-generic.

I do not have a ethernet connection without moving everything to another room so I'll try that soon. It did come with an instillation cd but it is the micro type and my pc can only take the full size. Is there a way to take the necessary stuff off the dvd and put it in a different computer to put it on a usb? Also if necessary I would update to 16.04 to get it to work.

Edit:
After looking at the dvd in another computer all the drivers are for windows.

---

### Post by nanth on 2016-09-07
[SIZE=6]SOLVED!
 
[SIZE=3]I installed bcmwl-kernel-source and I am posting this from my new pc without an ethernet connection!

Thank you SO much [ 						 							]("https://ubuntuforums.org/member.php?u=35909")[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909")[/SIZE][SIZE=3] for your help![/SIZE]
[/SIZE]

---

