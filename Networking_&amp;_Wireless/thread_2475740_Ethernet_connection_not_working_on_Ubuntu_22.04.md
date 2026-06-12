---
title: "Ethernet connection not working on Ubuntu 22.04"
date: 2022-06-07
forum: Networking &amp; Wireless
---

### Post by mihail-finsbury on 2022-06-07
Hello,

Ethernet connection is not working on Ubuntu 22.04. My WiFi connection is fine, however I can not use the wired connection after upgrading from 20.04 to 22.04. Both used to work fine with the old distribution.

 Thanks in advance.


```
dpkg -l linux-* | grep ii
ii  linux-base                             4.5ubuntu9                      all          Linux image base package
ii  linux-firmware                         20220329.git681281e4-0ubuntu3.2 all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-22.04                5.15.0.35.38                    amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.15.0-33                5.15.0-33.34                    all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-33-generic        5.15.0-33.34                    amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-5.15.0-35                5.15.0-35.36                    all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-35-generic        5.15.0-35.36                    amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-22.04        5.15.0.35.38                    amd64        Generic Linux kernel headers
ii  linux-image-5.15.0-33-generic          5.15.0-33.34                    amd64        Signed kernel image generic
ii  linux-image-5.15.0-35-generic          5.15.0-35.36                    amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04          5.15.0.35.38                    amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   5.15.0-35.36                    amd64        Linux Kernel Headers for development
ii  linux-modules-5.15.0-33-generic        5.15.0-33.34                    amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-5.15.0-35-generic        5.15.0-35.36                    amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-33-generic  5.15.0-33.34                    amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-35-generic  5.15.0-35.36                    amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu7            all          base package for ALSA and OSS sound systems


sudo lshw -c network
  *-network UNCLAIMED       
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:e1a00000-e1a1ffff memory:e1a80000-e1a80fff ioport:4080(size=32)
  *-network
       description: Wireless interface
       physical id: 4
       bus info: usb@2:1.3
       logical name: wlx00367661ddfa
       serial: 00:36:76:61:dd:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=5.15.0-35-generic firmware=N/A ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11


```

---

