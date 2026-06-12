---
title: "How to connect to internet ???"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by anubhav2k on 2008-10-21
I have a ethernet and WiFi modem ........... how can i connect to internet, i don understand, using linux for 1st time >?

---

### Post by Joeb454 on 2008-10-21
Moved Thread out from the Forum Archive :)

Sorry about that :p

---

### Post by Hyper Tails on 2008-10-21
left click on the network icon on the top panel and select which wifi network you want

---

### Post by Kevbert on 2008-10-21
We need to check if you need firmware drivers. Go to Applications-Accessories-Terminal and enter the following
```
lspci
iwconfig
lshw -C network
```
(note a large C on the last one).  For each of these commands there will be an output. Select the output from each command in turn with your mouse so that it is highlighted and press Ctrl-Shift-C (to copy) and Ctrl-V to paste into a new post here.

---

