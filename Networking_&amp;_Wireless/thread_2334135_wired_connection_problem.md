---
title: "wired connection problem"
date: 2016-08-16
forum: Networking &amp; Wireless
---

### Post by miragemosaic on 2016-08-16
Hello, 
I have an old laptop and i decided to put ubuntu on it trying to move away from W10. I installed Ubuntu 16.04.1 LTS, but now im having a little problem with my wired internet connection but the wifi works. I get this "Disconnected - you are now offline". I did some research on my own, but since im new to linux i need some opinion and maybe a solution.
So i ran lspci -knn in terminal and i get this message regarding my lan card/driver:

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
      Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:306a]
      Kernel driver in use: r8169
      Kernel modules: r8169

 Does this mean i dont have the right driver for my lan card and this is the problem?

---

