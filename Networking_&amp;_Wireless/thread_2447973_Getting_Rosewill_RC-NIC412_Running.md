---
title: "Getting Rosewill RC-NIC412 Running"
date: 2020-07-29
forum: Networking &amp; Wireless
---

### Post by shorthand1121 on 2020-07-29
Referring to [https://ubuntuforums.org/showthread.php?t=2397677](https://ubuntuforums.org/showthread.php?t=2397677), the Linux guru at work just helped me out of a pinch and has some additional notes on how to compile the driver to get these cards working in Ubuntu.

```

STEPS TO BUILD AND INSTALL TEHUTI TN9710P DRIVER
07/29/2020


-- install the card in the chassis, then power on


-- update and upgrade the system
# apt update
# apt -y upgrade
# reboot


-- verify the card is visisble to the os
# lspci


-- prepare Ubuntu for the module build
# apt install module-assistant
# m-a prepare


-- download the driver tgz from Tehuti
http://www.tehutinetworks.net/?t=drivers&L1=8&L2=12&L3=26&L4=0&L5=0&L6=0&L7=0&sent=true


-- explode the tgz file
# tar -xvpf tn40xx-0.3.6.17.3.tgz


-- read the "Readme" file in the "tn40xx-0.3.6.17.3" build dir


-- check the card version and find that the card is the TN9710P and requires the Marvell PHY hdr
# lspci | egrep "TN"


-- search around the forums and hints and notes until you find someone that posts a link to the
   required .hdr file of "x3310fw_0_3_4_0_9445.hdr".  I found it here...
https://www.gitmemory.com/issue/acooks/tn40xx-driver/3/474259259


-- unzip the downloaded file
# gunzip x3310fw_0_3_4_0_9445.hdr.gz


-- get the file into the "tn40xx-0.3.6.17.3" directory
# cp x3310fw_0_3_4_0_9445.hdr tn40xx-0.3.6.17.3/.


-- build and install
# cd tn40xx-0.3.6.17.3
# make clean
# make all
# make install


-- kick off a rebuild of initramfs
# update-initramfs -u -k `uname -r`


-- test the module (note that the full path will very with kernel - use "find" worst case)
# insmod /lib/modules/4.15.0-112-generic/kernel/drivers/net/tehuti/tn40xx.ko
# lsmod | egrep tn


-- check that the network looks good now
# ifconfig -a
# ethtool DEVICENAME


-- verify that device is present on reboot
# reboot


-- check that the network looks good now
# ifconfig -a
# ethtool DEVICENAME


Reference and files are all present /root



```

---

