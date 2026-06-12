---
title: "Belkin usb dongle."
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by Jdm111 on 2007-12-17
Hi guys. 
When i start up my PC to get my wireless dongle working to get on the internet i have to disable in then re enable it by unticking the box and ticking it again on the network tool.

The dongle is a Belkin fd7050 and it is Ubuntu 7.10.

---

### Post by Jdm111 on 2007-12-18
Please help:(

---

### Post by rustybronco on 2007-12-18
Would you please post the output of lshw -C network and lsusb.

---

### Post by Jdm111 on 2007-12-18
joe@Joe-desktop:~$ lshw -C
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status


joe@Joe-desktop:~$ lsusb
Bus 003 Device 002: ID 050d:705a Belkin Components 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
joe@Joe-desktop:~$

---

### Post by rustybronco on 2007-12-18
joe@Joe-desktop:~$ lshw -C

"Would you please post the output of **lshw -C network** and lsusb

---

### Post by Jdm111 on 2007-12-18
> **rustybronco said:**
> joe@Joe-desktop:~$ lshw -C

"Would you please post the output of **lshw -C network** and lsusb

sorry
joe@Joe-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:c4:b7:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:ae:4d:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.4 multicast=yes wireless=IEEE 802.11g
joe@Joe-desktop:~$

---

### Post by rustybronco on 2007-12-18
***edit*** product: RTL-8139/8139C/8139C+ search for posts on this chipset.
No need to be sorry... I do this from work so my answers are sometimes short.

You may want to also try a different network manager.

---

### Post by Jdm111 on 2007-12-18
> **rustybronco said:**
> ***edit*** product: RTL-8139/8139C/8139C+ search for posts on this chipset.
No need to be sorry... I do this from work so my answers are sometimes short.

You may want to also try a different network manager.

Could not find anything. What do you suggest?

---

### Post by rustybronco on 2007-12-18
Try installing wicd (google it)

---

### Post by Jdm111 on 2007-12-18
> **rustybronco said:**
> Try installing wicd (google it)

Thank you soooo much i can't thank you enough!:):):):)

---

### Post by rustybronco on 2007-12-18
I take it worked.... ;) :)
welcome to the house of Linux, please thank those who came before me, from them I have learned...

---

