---
title: "2 system IP address on the same WiFi router"
date: 2023-05-10
forum: Networking &amp; Wireless
---

### Post by satimis on 2023-05-10
Hi all,

**[COLOR="#FF0000"]Same WiFi router[/COLOR]**

Wired IP address assigned to PC = 192.168.1.xxx
WiFi IP address assigned to Android Phone = 10.98.31.xxx

They can't communicate.  On PC it can't ping 10.92.31.xxx

Please advise how to change the IP of Android phone to 192.168.1.xxx system

Thanks in advance.

Regards

---

### Post by HuTkW$* on 2023-05-10
Hi,
The problem is the following : you have 2 DHCP servers inside your home network ! That is really forbidden and problematic !
So you must identify, and deactivate the DHCP server one with  10.9...
Let the first DHCP server 192.168.1.X assign an IP address to your Android Phone, so they will ping each other.

---

### Post by satimis on 2023-05-10
> **exystenz said:**
> Hi,
The problem is the following : you have 2 DHCP servers inside your home network ! That is really forbidden and problematic !
So you must identify, and deactivate the DHCP server one with  10.9...
Let the first DHCP server 192.168.1.X assign an IP address to your Android Phone, so they will ping each other.
Hi,

Thanks for your advice.

Sorry, I have only 1 (one) DHCP (WiFi router) in house.  My Android phone (Samsung Galaxy S22 Ultra) has a SIM card.

After removing the SIM card the IP 10.98.31.xxx disappears.  Then I login DHCP (WiFi router) IP 192.168.1.xxx is assigned.  After reinstalling the SIM card the IP is still 192.168.1.xxx

I have no idea how IP 10.98.31.xxx comes?  Anyway problem is now solved.

Thanks again for your reply.

Regards

---

