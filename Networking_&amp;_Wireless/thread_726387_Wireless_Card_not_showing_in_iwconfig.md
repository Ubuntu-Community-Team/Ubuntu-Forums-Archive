---
title: "Wireless Card not showing in iwconfig"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by goodalt on 2008-03-16
I have installed LSIPNDS.inf driver for my WMP11 v4 Linksys card

This shows as installed using ndiswrapper -l

however, when i use iwconfig there is no wlan0 showing

Can anybody help??

---

### Post by kevdog on 2008-03-16
Does it show up with lshw -C network?

Did you load the ndiswrapper kernel module?
sudo modprobe ndiswrapper

---

### Post by goodalt on 2008-03-17
Shows uo in lshw -C network

but does not have a logical name and is showing as *-network UNCLAIMED

I will try the sudo modprobe ndiswrapper tonight and post back the results.

---

### Post by goodalt on 2008-03-17
I am quite new to Linux

Tried sudo modprobe ndiswrapper

command completed with no errors or messages

---

### Post by goodalt on 2008-03-18
Think I know why it won't work.

Card has 32-bit driver and I am running 64 bit OS

How do I re-install with 32-bit version clearing the 64-bit partition I already have.

I have a dual boot system for Windows XP

---

