---
title: "Lenovo G780, Ubuntu 12.04, Broadcom [14e4:4727] (rev 01), Wifi not working"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by R3B3LCAUSE on 2013-10-12
I am new to ubuntu, and I am having trouble getting Wifi to work. The default driver that installed when I installed ubuntu (brcmsmac I think)wouldn't show networks unless I was right next to the router, and it would disconnect after a minute or so. I tried using the "Proprietary STA Driver" from the system settings additional drivers, and It showed tons of networks, but It wont connect at all to any of them. Ive heard that my specific Broadcom Card (Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)) is difficult to get working. I tried to use the solution [here]("http://ubuntuforums.org/showthread.php?t=2080520&p=12336974#post12336974"), but when I tried to run those commands in the terminal I got:
"dpkg: error processing linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb"

Being new to linux I am not really sure what this means. Does anyone know how I can get my wireless working?

---

### Post by varunendra on 2013-10-13
Let me first have the privilege to Welcome you on the forums R3B3LCAUSE ! :)

The card you mentioned is well supported by the native brcmsmac driver in kernels later than 3.8. On kernels older than that, probably not so well, and yours IS a relatively older one.

To diagnose the problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

