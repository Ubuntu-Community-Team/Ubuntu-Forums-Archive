---
title: "Ubuntu 14.10 is not recognising my 3g usb modem"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by kumarsv.kiran on 2015-03-20
Hi all!

I am using ubuntu 14.10 utopic unicorn. I have trouble in installing and connecting the usb modem to the laptop. I started installing by trying the readme.txt file given in the usb modem itself. I have attached the readme.txt file to this thread. I can see the installed application as "LAVA 3G USB Modem" when I press the super key. But when I click the application nothing shows up. Usb modem is not listed in the network manager. I also tried the solution given in this link.

[http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04](http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04) 

But no solution works to my problem.

I tried lsusb in terminal and this is what I get:

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:8122 Suyin Corp. 
Bus 001 Device 005: ID 1c9e:f001 OMEGA TECHNOLOGY 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I can see my device ID is 1c9e:f001 and I have already installed usb-modeswitch , usb-modeswitch-data. I also installed the modem-manager GUI frontend to see if the driver is listed. This also didn't work.

I don't know what to do now.. Please help me in solving this problem

---

