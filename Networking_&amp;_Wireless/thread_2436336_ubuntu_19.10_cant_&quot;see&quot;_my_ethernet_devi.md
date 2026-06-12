---
title: "ubuntu 19.10 cant &quot;see&quot; my ethernet device"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by merlin5153 on 2020-02-04
hi guys im having an issue. I have tried to switch from wireless to wired but ubuntu just cant see my ethernet device any help or suggestions would be greatly appreciated

---

### Post by TheFu on 2020-02-04
What is the ethernet device according to the manuals that came with it?  You can try these commands too:

```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
sudo lshw -C network
```
The last one would be my preference since it shows the most data.

Really new devices might not have any drivers in the kernel. Bleeding edge problem.

---

### Post by merlin5153 on 2020-02-05
its the ethernet built into my motherboard so not sure what exactly it is.  this is what i get with sudo lshw -C network


```
 
      *-network                 
       description: Wireless interface
       physical id: 2
       bus info: firewire@4
       logical name: wlxa040a07cab9c
       serial: a0:40:a0:7c:ab:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb driverversion=5.3.0-29-generic firmware=0.0.00-b1 ip=192.168.1.75 link=yes multicast=yes wireless=IEEE 802.11

```


oh its an old B85 board so not exactly bleeding edge

---

### Post by merlin5153 on 2020-02-05
ok i found the problem but had to fix another issue to do so lol. system wasn't detecting keyboard input at boot up so had to unplug my OS drive to get into my bios and it turns out my ethernet was disabled in bios

---

### Post by TheFu on 2020-02-05
Please mark the thread as "SOLVED" using the **thread tools button** near the top.

If not solved, get out the manual and start reading.

---

