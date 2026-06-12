---
title: "Serial port detection w/2.4, not 2.6 kernel"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by steptayl on 2006-11-28
With a 160G hard-drive, no serial ata card and debian distributions  
that already are/or allow choice of kernel, 2.4 connects, 2.6 does not.

Using Sarge 3.1 or Knoppix 3.7  and a 2.4 kernel, the serial port is detected on ttyS1. Dialup works. 

After standard install of Dapper Drake and 2.6 kernel, no connection. /var/log/kern.log shows 
 "ttyS1: LSR safety check engaged!"

What is missing that would detect the serial port and allow connection without "safety check"?

The setserial module is installed; same "safety check"

Thanks in advance for assistance.

---

