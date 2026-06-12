---
title: "Mobile broadband connection not working"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by nahidbigboss on 2014-11-29
Hello,
I am facing this kinda problem from 3 days ago. I am unable to connect through Mobile Broadband. But its detect my modem (Snapshot-1 & snapshot-2). But whenever i click on "Warid Internet" its showing a popup message "Disconnected You are now offline", although i can connect through Wi-Fi.
Things i did:
- Delete "Warid Internet" and Re Add Mobile Broadband, still not working!
- Uninstall modem-manager and re installed, still not working!
- Uninstall and re installed usb-modeswitch, still not working!
 
Snapshot-1:
[IMG]http://tupla.wen.ru/images/Screenshot3.png[/IMG]

Snapshot-2:
[IMG]http://tupla.wen.ru/images/screenshot1.png[/IMG]

Please help!
Note: i'm not expert user so, please use human readable english :-#

---

### Post by nahidbigboss on 2014-11-29
for the record this is my lsusb output:

```
bigboss@ubuntu:~$ lsusb
Bus 002 Device 004: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 006: ID 0421:0223 Nokia Mobile Phones 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0a5c:21e3 Broadcom Corp. HP Portable Valentine
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ccooi on 2014-11-30
Please at least post the log messages.
You can easy find them in /var/log/syslog, or view it with the command dmesg.

---

