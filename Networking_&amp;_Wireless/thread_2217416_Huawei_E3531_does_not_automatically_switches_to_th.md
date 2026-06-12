---
title: "Huawei E3531 does not automatically switches to the modem"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by tamir2 on 2014-04-17
So there usb modem Huawei 3531 and the operating system does not see the modem, maybe because of what USB-modeswitch not automatically connect your device as a modem. Please help supplement the _r_eport - [https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/1308895](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/1308895) - any useful information to solve this problem.

---

### Post by JALINDAR on 2014-05-19
Hi Tamir2,

follow the lines below to get E3531 working with Ubuntu 12.04.

1. connect E3531 to the Ubuntu 12.04 PC.

2. Check vid :  pid of the modem using $lsusb . It should be 12d1:1506

3. Load the option drivers to ram using $modprobe -v option

4. register vid : pid of the modem to the option driver using $echo "12d1 1506" >/sys/bus/usb-serial/drivers/option1/new_id

5. check if ttyUSB device is detected for the modem or not using $dmesg | tail

6. Configure your "Mobile Broadband" in "Network Connections" on the right top corner of the  Ubuntu 12.04. Set dial no,apn , user, pass ....
also enable mobile broadband.

It should be working all ok with this setting.

---

