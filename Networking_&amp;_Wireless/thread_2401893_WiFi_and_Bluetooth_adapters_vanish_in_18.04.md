---
title: "WiFi and Bluetooth adapters vanish in 18.04"
date: 2018-09-24
forum: Networking &amp; Wireless
---

### Post by tapasray on 2018-09-24
I had been running 18.04 as dual-boot default os on an originally Windows 10 HP notebook until one of the updates. After that update, the wireless and Bluetooth adapters disappeared. Please help!!

---

### Post by tapasray on 2018-09-24
PS: I am unable to get and run the wireless info script, or even take the initial step of updating as per the instructions given here, since my notebook does not have an Ethernet port. I tried to use an Ethernet-USB adapter, but got no connectivity.

---

### Post by jeremy31 on 2018-09-24
Try booting into and older kernel and see if wifi and Bluetooth function

---

### Post by tapasray on 2018-09-24
Will do. Thanks. Meanwhile, I managed to run the wireless info script by copying it from another thread in this section. The output is:

 XXyyzz:~$ sudo lshw -class network
  *-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:91100000-91101fff
:

---

### Post by tapasray on 2018-09-24
Ok, I booted with kernel 33 instead of 34, and got the wifi and Bluetooth back. Thanks again! Now, how to get these back in 34?"

---

### Post by jeremy31 on 2018-09-24
I have a hunch, post results for ```
dpkg -l | grep 4.15.0-34
```

---

### Post by tapasray on 2018-09-24
Thanks!

xxyyzz:~$ dpkg -l | grep 4.15.0-34
ii  linux-image-4.15.0-34-generic                 4.15.0-34.37                        amd64        Signed kernel image generic
ii  linux-modules-4.15.0-34-generic               4.15.0-34.37                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP

---

### Post by jeremy31 on 2018-09-24
Try ```
sudo apt install --reinstall linux-modules-extra-4.15.0-34-generic
```
Then reboot into -34

---

### Post by tapasray on 2018-09-24
Did that and let it reboot to default. I am assuming that it rebooted to 34. Anyway, wifi and Bluetooth are back. So, solved. Many, many thanks! Really appreciate your help. 

I'll just manually reboot to 34 before marking this thread as solved.

---

### Post by tapasray on 2018-09-24
Did that. Wifi and Bluetooth are back. Many, many thanks! Really appreciate your help. 

Marking this thread as 'solved'.

---

