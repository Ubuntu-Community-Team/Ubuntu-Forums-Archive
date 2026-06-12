---
title: "Ubuntu 18.09 on HP laptop does not see built in wifi adapter"
date: 2019-05-20
forum: Networking &amp; Wireless
---

### Post by kulaywolf on 2019-05-20
I have Ubuntu 18.09 as dual boot for my HP laptop I got last year I think.  My problem I want to solve first I guess is that the built in wifi adapter does not work.  I can connect to the internet via tethering via my iPhone, but that speed is not fast.  I do not know where my Ethernet cables are so until I can get wifi working with ubuntu I can only use my tethering ability from my phone.

I asked someone how to fix my wireless problem, but I think I asked the wrong person.  He suggested that I do diagnosis or get help from hp main website.  I showed him what version of Ubuntu I was using but he did not seem to understand what that meant.  I doubt it is a hardware problem but a driver problem.  I do not know how to get the new driver on my ubuntu part of the computer.

---

### Post by kc1di on 2019-05-20
We need to know what wireless card you have in that machine.  It's usually just a driver problem. 
Please go to a terminal and enter this command and post the output you get.  ```
lshw -C network
```

---

### Post by kulaywolf on 2019-05-21
```
*-network UNCLAIMED
       description: Network controller
       product: RTL8723DE 802.11b/g/n PCIe Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b1000000-b100ffff
```
Sorry I forgot to do this earlier.

---

### Post by SeijiSensei on 2019-05-21
Make sure you didn't accidentally turn the adapter off at the keyboard.  I've done that on occasion with an HP laptop and spent a good chunk of time wondering why my wifi connection did not work.

---

### Post by kulaywolf on 2019-05-21
I know I am unable to install Blender but would this be the same reason I cannot install a WiFi driver?

---

### Post by mel-blanc on 2019-05-21
Just as a possible chance.

When installing the 18.10 you are prompted at the 3rd popup window 
labeled Updates & other Software to select the Normal or Minimal 
Installation. Right under that option in the same popup is 'Other Options".
Just below other options is a checkbox for: "Install third-party software
for graphics and WiFi Hardware".

Did you check that box?

I discovered the hard way that not selecting that option and then trying 
to install the WiFi drivers manually after installing the OS was a good way 
to learn a lot of new expletives. 

YMMV

---

### Post by jeremy31 on 2019-05-21
Please see [https://ubuntuforums.org/showthread.php?t=2419146&p=13860650#post13860650](https://ubuntuforums.org/showthread.php?t=2419146&p=13860650#post13860650)

---

### Post by kc1di on 2019-05-21
The reason you can not install blender may be that you have another package manager running.  Try rebooting and try the install again. 
Good luck.

---

