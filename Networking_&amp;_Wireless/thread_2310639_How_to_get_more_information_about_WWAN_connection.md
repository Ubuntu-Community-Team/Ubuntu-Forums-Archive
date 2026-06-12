---
title: "How to get more information about WWAN connection?"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by sergei-redleafsoft on 2016-01-20
I know it is good to have it working out of the box, so I am really nitpicking here, but the Network Manager doesn't show any specifics about WWAN connection. I have Sierra EM7355 aka Gobi5000 card, and it is detected automatically in 15.10, and I can connect, but it would be nice to have some extras like the Windows connection tool has. For example, I have no idea what networks are available and what speed I have connected with. The card is capable of LTE, UMTS, HSPA and GPRS, so it would be nice to have access to these details. Is there a package that can help me to get these details in some sort of status GUI?

---

### Post by ajgreeny on 2016-01-21
Click on the network icon in the panel and it should show the various networks available to you as well as other items you can use, eg Connection Information and an Edit option.

There is also the commands ifconfig for ethernet and iwconfig for wifi which will give you a lot of info about the connection you have at that time.

---

### Post by sergei-redleafsoft on 2016-01-21
This question is about WWAN (mobile wireless) not WLAN (wifi). I have found that mmcli can get some extra information in command line. 

The number changes each time I suspend the laptop, but here's the isuea: **mmcli -m 3  --simple-status**

---

