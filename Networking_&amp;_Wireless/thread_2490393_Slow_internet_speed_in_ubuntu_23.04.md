---
title: "Slow internet speed in ubuntu 23.04"
date: 2023-09-02
forum: Networking &amp; Wireless
---

### Post by praveen050 on 2023-09-02
while connecting directly with the router, the internet speed is around 1mb/s, whereas when my mobile is connected to wifi and using mobile hotspot speed of 20mb/s is reached.I have tried all the solutions posted in this [https://blog.rottenwifi.com/ubuntu-slow-internet/](https://blog.rottenwifi.com/ubuntu-slow-internet/)
And this problem is only observed only on 23.04 version, since i have used 22.04 for past week. the output for 

lshw -C network

*-network                 
       description: Wireless interface
       product: Comet Lake PCH-LP CNVi WiFi
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 00
       serial: dc:1b:a1:bd:0f:e2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.2.0-31-generic firmware=72.daa05125.0 QuZ-a0-jf-b0-72.u

Looking forward for the answer. Thanks in advance...

---

