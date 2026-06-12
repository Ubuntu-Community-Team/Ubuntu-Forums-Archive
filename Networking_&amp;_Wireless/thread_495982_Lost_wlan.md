---
title: "Lost wlan"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by glendavee on 2007-07-08
My wireless connection has suddenly disappeared. I was connected using wlan1. When I look for it using  iwconfig, it isn't there. 
david@david-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

How do I get it back???

---

### Post by fredj on 2007-07-09
Open a terminal. Type 'lshw -class nework' (without the quote marks). Post the
result here.

---

### Post by glendavee on 2007-07-09
lshw - class network    result is 

WARNING: you should use this program as a super-user
  *-network
       description : Ethernet interface
       product:  88E8055 PCI-E Gigabit Ethernet Controller
       vendor   Marvel Technology Group Ltd
       physical id:0
      bus info:   pci@04:00.0
      logical name: etho
     version:   10
     serial:  00:16:36:fd:09:c5
      width: 64 bits
      clock:  33MHz
      capabilities:  bus_master cap_list ethernet physical
     configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 multicast=yes
      resources: iomemory:da000000-da003fff ioport:3000-3-ff  irq:18

Does this make any sense??

---

### Post by kevdog on 2007-07-09
Do you have a wried connection on your computer?  The device listed below is associated with eth0.  I just want to make sure this is the wireless device rather than a wired device.

---

### Post by glendavee on 2007-07-09
Yes, I use a wired connection also. What I don't understand is why wlan1 (and wlan0)  has disappeared completely. When I look for it using Connection Properties, the connection is listed, but the status is "error" When I try to reconfigure it, I get "the interface does not exist"

---

