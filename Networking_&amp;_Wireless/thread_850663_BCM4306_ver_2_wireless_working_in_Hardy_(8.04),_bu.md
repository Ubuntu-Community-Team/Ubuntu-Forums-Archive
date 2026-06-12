---
title: "BCM4306 ver 2 wireless working in Hardy (8.04), but not through reboot."
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by simonz on 2008-07-05
After reading many posts of the Linksys WPC54G PCMCIA Wireless (Broadcom 4306 chipset) adapter, I have it partially working with Hardy 8.04.  The problem is that when I reboot, it doesn't automatically reconnect, and I have to run a manual script to get it connected again.

Here is the script that I run after each reboot which enables the wlan0 and the Internet.

sudo ifconfig wlan0 down
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ndiswrapper
sudo rmmod ssb

sudo modprobe ndiswrapper
sudo modprobe ssb 
sudo ifconfig wlan0 up

I've tried many of the work arounds in this forum from modifications to init.d to installing Wicd.  Nothing helps.

Does anyone have any ideas of any way to have the BCM4306 come up automatically after a reboot?

simonz

---

