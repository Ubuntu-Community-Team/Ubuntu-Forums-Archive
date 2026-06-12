---
title: "Lost both wifi and wired connection in both Ubuntu and Fedora"
date: 2018-04-24
forum: Networking &amp; Wireless
---

### Post by stjepan.poljak on 2018-04-24
I have been using both Ubuntu and Fedora for the last six months  without any issues. After coming from work today, I see there is no  internet connection, wired or wifi both in Fedora and Ubuntu, but on  Windows works fine. I have searched and searched through forums, nothing  helped. Have tried previous kernels and recoveries to no avail. Here  are outputs of some commands suggested...
  
lshw -C network

*-network               
     description: Network controller
     product: BCM43227 802.11b/g/n
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:03:00.0
     version: 00
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: driver=bcma-pci-bridge latency=0
     resources: irq:17 memory:d1800000-d1803fff

ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62112 (62.1 KB)  TX bytes:62112 (62.1 KB)

lspci | grep -i network

03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n

lsmod | grep -i b43

b43                   417792  0
mac80211              782336  1 b43
cfg80211              614400  2 b43,mac80211
ssb                    57344  1 b43
bcma                   57344  1 b43

  Any help would be appreciated. Thank you in advance.

---

### Post by TheFu on 2018-04-24
I don't see any wired ethernet above.  **So, did the NIC fail?   **

You say Windows works - is that a different computer or the same?  If different, swap the cables between the machines.

Can't help with wifi. Sorry.

---

### Post by stjepan.poljak on 2018-04-25
Ubuntu and Windows are, of course, on the same machine, Fedora is on a USB stick and was plugged in to the same machine, so the NIC did not fail, Linux failed, a blind guess is again some meaningless kernel update; for last seven years of using Linux-based OS, I never had these problems. Why do I have them now? If I could get some help with this, it would be appreciated. Wifi is not important for now, let's just get my ethernet up and going, which should be a basic functionality, by the way.

---

### Post by chili555 on 2018-04-25
> a blind guess is again some meaningless kernel update; There are no meaningless kernel updates. Each comes with security, driver, performance and other updates that are crucial to most of us, but perhaps not exactly to you.> let's just get my ethernet up and going, which should be a basic functionality, by the way.You have provided no information about your ethernet. Please let us see:```
lspci -nnk | grep -e 0200 -e 0280
```Do you believe that b43 and its associated firmware are correct for your wireless? I don't think so. Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by stjepan.poljak on 2018-04-25
Here is the output...

lspci -nnk | grep -e 0200 -e 0280

03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

And I have also ran that wireless-script and attached the log to it. Thank you for your time.

---

### Post by stjepan.poljak on 2018-04-25
Forget about it. I have reinstalled Ubuntu and realized it does not work anyway. So, I saw that on Windows it only connects to Wi-Fi, but that ethernet is screwed. I have managed to get my wireless to work on Ubuntu, but no ethernet anywhere. I guess it could be a malfunction in the NIC afterall...? Thanks anyway.

---

### Post by chili555 on 2018-04-25
>  I guess it could be a malfunction in the NIC afterall...?It appears so. Sorry.

---

### Post by TheFu on 2018-04-25
Please mark the thread as solved above - thread tools. This helps the community.

---

