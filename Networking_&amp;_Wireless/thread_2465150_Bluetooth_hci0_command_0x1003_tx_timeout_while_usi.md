---
title: "Bluetooth: hci0: command 0x1003 tx timeout while using hciattach on ubuntu 20.04"
date: 2021-07-23
forum: Networking &amp; Wireless
---

### Post by ganesh7095955655 on 2021-07-23
Downloaded and flashed the  "ubuntu-20.04.2-minimal-armhf-2021-02-07.tar.xz" file as rootfs to  embedded board and trying to connect to bluetooth using below commands.
 $ hciattach -t 30 /dev/ttymxc0 any 115200 flow
$ hciconfig hci0 up
$ hcitool scan
 sometimes its connecting and able to scan the devices but sometimes its throwing below errors while giving hciattach command.

     root@arm:~# hciattach -t 30 /dev/ttymxc0 any 115200 flow
    Device setup complete
    [  114.330384] Bluetooth: hci0: Frame reassembly failed (-84)
    root@arm:~# [  114.338664] Bluetooth: hci0: Frame reassembly failed (-84)
    [  116.349037] Bluetooth: hci0: command 0x1003 tx timeout

    [  118.365040] Bluetooth: hci0: command 0x1001 tx timeout

    [  120.381037] Bluetooth: hci0: command 0x1009 tx timeout

kernel version linux-imx 5.4
ubuntu version 20.04
ble module qca9377 based
 What might be the issue . and how to resolve it. Thanks in advance.

---

