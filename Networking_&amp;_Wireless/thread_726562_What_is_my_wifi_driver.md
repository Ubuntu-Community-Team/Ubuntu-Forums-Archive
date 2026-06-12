---
title: "What is my wifi driver?"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by mr tim esquire on 2008-03-16
Hi, im following the wifi setup guide at the community pages.
under iwconfig i have wifi0 and wlan0.
i want to disable wifi0 but im not sure how to do this.
community pages say the following:-
```
ubuntu-7.10# gksu echo "blacklist hostap" >> /etc/modprobe.d/blacklist-orinoco
ubuntu-7.10# gksu echo "blacklist hostap_ap" >> /etc/modprobe.d/blacklist-orinoco
```
where 'orinoco' is the wifi driver.
How do i know what my wifi driver is?
out put under lspci is:-
00:10.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

thanks!

---

