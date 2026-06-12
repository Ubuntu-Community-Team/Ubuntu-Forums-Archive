---
title: "Can not connect to internet"
date: 2020-01-07
forum: Networking &amp; Wireless
---

### Post by ck722 on 2020-01-07
In a brand new installation with Ubuntu 19.10, I can not connect to my wired internet. When I used older releases I did not have this kind of trouble. I really do not know what to do. My card is a RealTech 8139, use optical fibre, use ipv4 automatic IP

---

### Post by rbmorse on 2020-01-07
what is the output of:

> service network-manager status

---

### Post by ck722 on 2020-01-08
Not necessary anymore. I explain: using Ubuntu ISO I tried it without installation using **unetbootin-windows-675.exe. **I had an perfect internet connection. I saw wich were caracteristics of the connection and then, using my normal Ubuntu 19.10 put these settings into it. Worked! Solved! Thanks

---

### Post by rbmorse on 2020-01-08
Glad you got it going.

---

### Post by sandr115a on 2020-01-09
A reconfigured or malfunctioning router will prevent all your devices from connecting to the Internet [[FONT=Arial][COLOR=#000000]upsers[/COLOR][/FONT]]("https://www.upsers.review/")[COLOR=#000000].[/COLOR]

---

### Post by DanPerecky on 2020-01-20
I had a weird problem last week... the Wired connection.. for Virtual Box / Ubuntu worked one day...  The next day Virtual Box / Ubuntu's internet would not connect. WiFi on Windows 7- the host OS, was fine.

The solution was to go into Virt Box | Settings | Network | Advanced and change the MAC Address for the Ubuntu guest system.

..

---

