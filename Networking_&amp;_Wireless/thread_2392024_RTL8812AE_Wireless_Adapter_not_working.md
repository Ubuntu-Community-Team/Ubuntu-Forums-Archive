---
title: "RTL8812AE Wireless Adapter not working"
date: 2018-05-15
forum: Networking &amp; Wireless
---

### Post by azaan7 on 2018-05-15
Hello all,

To start, I must say that I am brand new to Linux and Ubuntu, I only know basic commands. I am dual-booting Windows 10 and Ubuntu 18.04 on a desktop PC. On Windows 10, when I plug in my PCIe WiFi adapter, it blinks green the entire time, and I get WiFi. On Ubuntu, however, there is no light, and there are no wifi signals. I write this post on a laptop that doesn't use Ubuntu, and using this laptop I can bring files to it via USB. How can I get Ubuntu to use my RTL8812AE PCIe adapter to look for WiFi? By the way, I'm not talking about WiFi cutting out or slow WiFi, I'm saying the WiFi doesn't work at all, no connection whatsoever. 



Thanks.

---

### Post by cowmoo32 on 2018-05-16
You need the drivers - [URL="https://github.com/lwfinger/rtlwifi_new"]https://github.com/lwfinger/rtlwifi_new
[/URL] 
The 88**12**ae drivers aren't there, just the 88**21**ae.  I had general connectivity issues and the 21 drivers fixed it, but I'm still not able to connect to 5Ghz [https://ubuntuforums.org/showthread.php?t=2391793](https://ubuntuforums.org/showthread.php?t=2391793)

edit: It seems that network-manager might be the culprit [https://github.com/lwfinger/rtlwifi_new/issues/195](https://github.com/lwfinger/rtlwifi_new/issues/195)

---

### Post by azaan7 on 2018-05-16
Thanks for the reply, I just had a question. I followed the instructions on the "Read Me", but I can't find the "<<Your Wireless Driver Code>>". I did "lspci | grep wireless", and I get this:

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter (rev 01)

Which part of this is the driver code? I ask this because when it tells you to do "sudo modprobe -r <<Your Wireless Driver Code>>", I don't know what to put in that. Steps in front of that also need it as well, any ideas?

---

