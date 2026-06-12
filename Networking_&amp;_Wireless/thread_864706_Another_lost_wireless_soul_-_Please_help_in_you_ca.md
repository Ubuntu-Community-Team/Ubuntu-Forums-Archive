---
title: "Another lost wireless soul - Please help in you can"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by jluquette on 2008-07-19
Can't connect - don't even have wireless as a choice.  Must have read a hundred of these threads - all seem to have similar problem but nothing I try works.  I have a Compaq Presario C762NR with a RT54G Linksys router.  Here's what I get when I type lshw -C network in a terminal window (I cut out the part with the ethernet card because the wired connection works just fine):


  *-network               
       description: Wireless interface 
       product: BCM4310 USB Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:21:00:19:03:c3 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

I have installed ndisgtk program and it seems to run fine.  However, it is asking me to point to a windows .inf file that I think is supposed to have the windows wireless driver that I need - but there are a thousand .inf files on my windows disk.  Which .inf file do I need and where can I find it?
   Also, as another little problem, when I go to System/Administration/Network all I have is a Wired and Point to Point choice - I don't even have a wireless choice that I could mess with!!
   If someone could just help me with these two teeny-weeny problems, maybe I could get this thing working.  My brother has already given up and gone back to Vista because of this - I refuse to be beat - help.:confused:

---

### Post by chili555 on 2008-07-20
Your *lshw* looks like you are half way home. Before we give up on the native driver, let's see if we can get going without Ndisgtk. Please open a terminal and do:```
sudo iwlist eth1 scan
cat /etc/network/interfaces
```Scanning may take a few moments, so be patient. Post the result here and we will proceed.

---

### Post by JagDragon on 2008-07-20
Looks like you are using a broadcom chip. I have made a tutorial to get broadcom chips going on the b43 native linux driver here: [http://ubuntuforums.org/showpost.php?p=5422091&postcount=2](http://ubuntuforums.org/showpost.php?p=5422091&postcount=2)

;)

---

