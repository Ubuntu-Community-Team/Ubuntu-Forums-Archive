---
title: "Ubuntu 22.04 &quot;No Wi-Fi Adapter Found&quot;"
date: 2022-10-30
forum: Networking &amp; Wireless
---

### Post by Dedalo on 2022-10-30
Hi there. After installing ubuntu 22.04 in my notebook (dell inspiron 3420), the wi-fi stoped working. In settings, when I look for wi-fi, it reads "No wi-fi adapter found".

 I've tried several things after reading on the internet, but none of them worked.

This is what lshw shows:
[INDENT]~$ sudo lshw -class network
  *-network DISABLED        
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 01
       serial: c0:18:85:e1:aa:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7c00000-f7c07fff


[/INDENT]
I don't know why it appears as "disabled", but anyway, I'm not allowed to "enable".

I tried switching along different options in the additional drivers menu in Software and updates, it doesn't work neither. I have already updated the system, and the problem persist.

Any hint on how to fix this issue?

Thanks in advance.

---

