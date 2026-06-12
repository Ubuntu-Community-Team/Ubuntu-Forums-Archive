---
title: "Realtek RTL8111/8168B with Feisty weird problem."
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by CrAzYoNi on 2007-04-18
Hi there,

I bough a new laptop, MSI Megabook L740, This laptop contain wifi card: Realtek RTL8111/8168B.

the system recognize the card:

> 
yoni@yoni-laptop:~$ sudo lshw -C network
  *-network               
       description Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.


> 
yoni@yoni-laptop:~$ lsmod | grep 81
l2cap                  28160  5 rfcomm
r8169                  35720  0 


& I have some weird problem with it, I can't connect to any wifi network, but I can see the wifi's around my system - What do i mean?

The network manager let me choose between several wifi networks that available in my area, but when I'm trying to connect to any of the networks it just hags for a minute & after it the interface get IP address 169.254 APIPA.

Do you might know how to solve this kind of problem?

Thanks in advance.

Yours, Yoni D.

---

### Post by josephus on 2007-04-19
the information you provided doesn't seem right to me.  can you post your complete output of sudo lshw -C network, and iwconfig ?  the realtek output looks like the stuff for your wired ethernet connection and not your wireless connection.  I think that you have Intel PRO/Wireless 3945ABG Mini-PCIe Card in your system. 

either way that doesn't seem to answer your question, since you say that you are able to see wireless networks around you but not connect.

the ip address you are getting is from the avahi/zeroconf system which assigns it's own address when it fails to get an address from the dhcp server.

------

these networks around you, are they yours or are they open networks?  what type of security are they using, and have you configured the passwords properly?  the best is if you can disable the security on the wireless routers and make sure that you can connect first before getting to the more complicated bit.

---

