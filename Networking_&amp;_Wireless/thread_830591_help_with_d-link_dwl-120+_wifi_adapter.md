---
title: "help with d-link dwl-120+ wifi adapter"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by hmfai on 2008-06-16
I am new to linux and try to get some helps.
i am running Ubuntu 8.04 and can't get my DWL-120+ to work;
i've searched the forum and still can't come up with a solution :(

here is the lshw -C network
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:40:05:31:7b:19
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

and lsusb
Bus 002 Device 005: ID 054c:0243 Sony Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 003: ID 2001:3b00 D-Link Corp. [hex] 
Bus 001 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000  

Thanks in advance :)

---

### Post by hmfai on 2008-06-17
bump
i searched google and came up with [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

how do i install the driver there? i compiled the source with the make command but what should i do next?
any help is appreciated

---

