---
title: "Load brcmsmac on boot in Ubuntu 14.04"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by med_malti89 on 2014-04-29
Hi All;
I am using Ubutnu 14.04 and I have installed aircrack-ng  suite but my wireless card (Broadcom BCM4313) unable to run monitor mode  because of the "wl driver" Otherwise, when I use Kali it works  perfectly because this one uses the driver "brcmsmac".
I tried to  disable the wl driver by modprobe command and activate the brcmsmac  manually and monitor mode was succefully activated (but wifi unable to  connect to network) . but I would like tto load the Broadcom driver at  startup and disable wl driver
is there a solution? thank you for helping me (excuse me for my english)

---

### Post by med_malti89 on 2014-04-30
Up

---

### Post by oktubr3 on 2014-05-12
> **med_malti89 said:**
> Hi All;
I am using Ubutnu 14.04 and I have installed aircrack-ng  suite but my wireless card (Broadcom BCM4313) unable to run monitor mode  because of the "wl driver" Otherwise, when I use Kali it works  perfectly because this one uses the driver "brcmsmac".
I tried to  disable the wl driver by modprobe command and activate the brcmsmac  manually and monitor mode was succefully activated (but wifi unable to  connect to network) . but I would like tto load the Broadcom driver at  startup and disable wl driver
is there a solution? thank you for helping me (excuse me for my english)

sudo apt-get purge --remove bcmwl-kernel-source
sudo modprobe -rv wl
sudo modprobe -v brcmsmac

---

### Post by wildmanne39 on 2014-05-12
Aircrack is not a supported topic on the forum so the thread has been closed. Your best option for support is on the Kali forum.

---

