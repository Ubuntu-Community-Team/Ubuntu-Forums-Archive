---
title: "Lubuntu 16.04 can't connect to wireless"
date: 2019-04-02
forum: Networking &amp; Wireless
---

### Post by sgroffman on 2019-04-02
Recently installed Lubuntu 16.04, everything works except does not recognize any wireless networks. Works fine with ethernet connection. Following advice [here]("https://www.datamation.com/open-source/overcoming-ubuntu-wi-fi-not-working.html"), I am trying to identify my wireless adapter and install the appropriate module, but am not sure how to tell which is my wireless adapter when I check through possible lists. Sudo lsusb returns this list: 

Bus 002 Device 003: ID 0a5c:21f3 Broadcom Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 5986:0299 Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I also am not sure if the solution is something more simple, like taking the system out of airplane mode. Unfortunately, the taskbar at the bottom of the screen has recently disappeared, so that is something else I'm working on fixing!

---

### Post by mörgæs on 2019-04-02
16.04 is out of support within a month. You will be better off with a fresh install of 18.04.

Please post back if the problem persists in 18.04.

---

### Post by sgroffman on 2019-04-11
Installed 18.04, wireless working great thanks!

---

