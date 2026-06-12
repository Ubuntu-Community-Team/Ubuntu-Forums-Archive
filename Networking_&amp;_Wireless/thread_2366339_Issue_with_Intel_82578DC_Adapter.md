---
title: "Issue with Intel 82578DC Adapter"
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by garras7 on 2017-07-16
Hi everyone,
I've encountered an issue with my Intel 82578DC Gigabit Ethernet Adapter on my Acer Aspire M7811 on Ubuntu 16.04 x64
I'm currently not able to see my adapter in the NetworkManager,

both **ifconfig** and **ifcongif -a** shows only lo ( I have no WiFi adapter )

**lspci** identifies
```
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
```

My machine has dual boot and in Windows 10 I can see the adapter listed in the Device Manager but i cannot connect.
Previous to yesterday, both on Windows and on linux the adapter was working perfectly.

I've tried booting a Ubuntu 17.04 Live USB to see if it was able to see the device but I'm facing the same results.

I've also checked in the BIOS and the adapter is [Enabled]

I'm starting to suspect that it might be a hardware fault or that i somehow disabled it. (?) 

Thanks in advance for the help

---

### Post by garras7 on 2017-07-16
Update: Now apparently the adapter on Windows works

---

### Post by BenginM on 2017-07-16
Salutations! and Welcome to the forums , please run the wierless script from the main networking & wireless sticky page , and paste the result here in [CODE] tag. and alos post the result of $ sudo lshw -C network

 thanks

---

