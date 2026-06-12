---
title: "Internet Problem Realtek driver RTL8723BE and no ethernet on UBUNTU Live"
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by alex_likes_linux on 2015-01-14
Hello Everyone,

I am trying Ubuntu Live from a USB (not full install) on my new laptop and I can't connect to the wifi. It appears to me that the driver is not present. I've tried to follow other posts and solutions, but my new laptop doesn't have an ethernet port, so I can't get the drivers that way. wireless.kernel.org appear to have drivers, but I don't know how to install them from a USB. I've got limited linux experience, but I'm learning (slooooowly).

Running lspci

I get 

01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

I wanted to test Ubuntu using the "live" version as this laptop has a touchscreen, but I'm happy to go for the full install if that helps.

In Summary

[LIST]
[*]Cannot detect any wifi networks or switch wireless on
[*]Assumed no wireless adapter driver
[*]No access to internet on that laptop
[*]Internet access on another PC
[*]Realtek RTL8723BE wireless card
[*]Ubuntu Live 14.04
[/LIST]

I appreciate any help that anyone can offer. Thanks for reading this far!

Alex

---

### Post by Himmagery on 2015-01-15
You'll need Ubuntu 14.10 to get it to work, but support for the RTL8723be in Linux isn't very good at the moment (but it is improving).  That said, I'm sending this from an Ubuntu machine with that chip in it, so it does work.

---

### Post by alex_likes_linux on 2015-01-15
Wow! It was that easy! That is fantastic, thank you very much Himmagery for taking the time to read and respond. I very much appreciate it. To confirm, I downloaded 14.10. Created a new USB and was then able to connect to the wifi with Ubuntu live. Bingo!

---

