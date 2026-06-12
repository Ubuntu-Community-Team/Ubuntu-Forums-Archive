---
title: "Flaky 802.11b behavior new on Edgy"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by ebeyer on 2006-11-05
I have a kit PC that uses a Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (PCI-based) wi-fi card.

On Dapper Drake (6.06), wifi worked 'right out of the box'.  In fact, this was one of the great things that distinguished Ubuntu for me from other linux distributions.

I recently did a clean install (reformatted the whole drive, repartitioned) of Edgy Eft (6.10).  I've been using it for a couple of weeks now, but never got the WiFi to work consistently.  Once in a blue moon it would connect to my home network (Apple Airport Extreme Base Station (802.11b/g) with  no WEP/WPA), but usually it would not.  On kwifimanager, it would see the home network, but when I try to switch to that network, it would just say 'Connection Failed'.  

My present work-around is to have a wired connection handy for backup.  However, this is not a long-term solution, particularly as I have designs of trying to integrate this machine into our office network, which uses a Linksys wireless router with WEP/WPA set up.

Any thoughts on debugging this issue are truly appreciated.

EB
](*,)

---

### Post by FrodoB on 2006-11-05
Unless there is a special reason, I would file a bug report and then install 6.06, it does have long term support after all.

---

### Post by ebeyer on 2006-11-05
Well, Edgy works fine with ethernet attached.  I should file a bug report, maybe.

---

