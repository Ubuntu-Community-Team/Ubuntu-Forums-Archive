---
title: "Bluetooth not working (grayed out) on Ubuntu 20.04"
date: 2022-03-14
forum: Networking &amp; Wireless
---

### Post by mohamedsouleimanepiro on 2022-03-14
Hello,


Since I installed Ubuntu 20.04 LTS, bluetooth is not enabled and grayed out. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290148&stc=1[/IMG]


Can you pls advise me, 

Here is my computer infos: 

Intel® Core™ i7-8565U CPU @ 1.80GHz × 8 

HP Laptop 15-da1xxx (6VK18EA#BH4) CND9461HDK

Wireless properties
                RTL8821CE 802.11ac PCIe Wireless Network Adapter
                Realtek Semiconductor Co., Ltd.
      



Thanks,

---

### Post by robertwk on 2022-03-14
I either had to install a bluetooth driver manually for it to work, or I had to go to "Session and Startup" and add blueman-applet as a startup service.

---

