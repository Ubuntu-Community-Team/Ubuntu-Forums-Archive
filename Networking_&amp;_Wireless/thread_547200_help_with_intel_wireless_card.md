---
title: "help with intel wireless card"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by newbie_123 on 2007-09-09
I am new to ubuntu and running one with wubi in vista. I have  Intel Pro 4965 agn wireless card. when I tried lshw -businfo (or something like) command,  in network class it only shows "Intel Corporation" but not full detail of the card. I dont know what to do. Please can any body help.

---

### Post by moore.bryan on 2007-09-09
[I]try these commands and post the results:
```
iwconfig
lspci
sudo lshw -C network

```
[/I]

---

