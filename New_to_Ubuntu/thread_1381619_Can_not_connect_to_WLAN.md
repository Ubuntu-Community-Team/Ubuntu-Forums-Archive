---
title: "Can not connect to WLAN"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by pawank on 2010-01-15
I loaded ubuntu 9.10. Can not connect to internet as network manager does not show wireless option .... only Wired Network and VPN is lsited.
What to do?
I am brand new to ubuntu.

---

### Post by mikewhatever on 2010-01-15
Start by identifying what wireless card you have. Open Applications->Accessories->Terminal and look at the output of the following command:

lspci | grep -i network

Post the output if possible.

---

