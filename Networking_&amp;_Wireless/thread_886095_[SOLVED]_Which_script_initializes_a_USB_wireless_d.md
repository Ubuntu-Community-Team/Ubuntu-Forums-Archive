---
title: "[SOLVED] Which script initializes a USB wireless device once it is plugged in?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by MonctonJohn on 2008-08-10
Here's the story. I have DansGuardian, tinyproxy and firehol working on my kid's computer. The issue is that the PC has a wireless usb adapter and when I reboot the PC after it gets an IP I always have to restart the three services for it to work. I would like to know which script sets up the wireless card and gives it an IP. I would like to insert some restart statements into this script so that I don't have to manually restart the three services. Any help is always appreciated.

---

### Post by MonctonJohn on 2008-08-11
There must be a script somewhere that calls dhclient???

Anybody know.

---

### Post by MonctonJohn on 2008-08-14
Well if anyone is looking for an answer to this or has a similar setup here it is:

There are scripts located in /etc/network/if-up.d/

You just need to write your own script to do whatever you want when your interface gets an IP. I put a script in there to restart tinyproxy, firehol and dansguardian.

---

