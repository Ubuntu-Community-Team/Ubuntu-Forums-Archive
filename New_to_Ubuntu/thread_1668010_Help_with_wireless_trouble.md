---
title: "Help with wireless trouble?"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by mindarson on 2011-01-15
I am new to Linux and Ubuntu.  I have installed Ubuntu 10.10 (Maverick Meerkat?)
on a USB and am using it on my Windows laptop that way.  

BUT - I cannot connect to my apartment building's wireless network!  

I have a Dell Inspiron 1501 laptop with a Dell Wireless 1390 WLAN Mini-Card, as well
as something called a "Broadcom 440x10/100 Integrated Controller."  Normally I work
under Windows Vista.

It's hard for me to give more information because I don't even understand what the 
problem is well enough to know what information is relevant to a solution. 

In my research into the problem, I've come across a lot of talk about drivers and 
a lot of talk about something called Ndiswrapper.  However, I've not come across any
user-friendly step-by-step guidance.  But maybe the nature of the problem precludes 
that.

Perhaps I should just spend more time getting to know the Ubuntu OS before worrying
about connecting to the Internet?  

If anyone is kind enough to help, please assume that I know next to nothing, because
I do!  Also, please don't send me to Ubuntu documentation, because I have been 
through it all and none of it has helped me.  

Thanks,

JC Knoll

---

### Post by corncob on 2011-01-15
Mentioning "Broadcom", you might be interested in this thread:
[http://ubuntuforums.org/showthread.php?t=1624032](http://ubuntuforums.org/showthread.php?t=1624032)

---

### Post by Miljet on 2011-01-15
If at all possible, you need to temporarily connect to the internet with a cable. Ubuntu will then prompt you to install any pending updates, which may or may not correct your problem. It will also automatically download any required drivers and offer to install them for you.

---

### Post by gordintoronto on 2011-01-15
The 10/100 is the controller for the wired Ethernet connection.

The Dell 1390 is also a Broadcom device, probably:
Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Have you run Administration/Additional Drivers? If it doesn't display anything, a temporary wired Internet connection would be really helpful.

---

### Post by akand074 on 2011-01-15
Yes, connect to a wired connection first. Then go to System > Administration > Additional Drivers and install your wireless drivers. Unfortunately there aren't working open-source drivers that can get your wireless working so you can use it to install the proprietary drivers.

---

### Post by walt.smith1960 on 2011-01-16
If you don't have access to a wired connection, there are a couple fairly simple choices.  You might be able to find a publicly accessible wired connection.  If you're in the U.S. I've used FedEx Office (formerly Kinkos). Plug in, do system -> administration -> Hardware drivers (this is Lucid-10.04) and see if Broadcomm is available to activate.  The other alternative is to buy a Wireless USB device that is plug & play.  I have a TrendNet TEW-424UB ver. 3.1 for just such purposes. There are other devices that are plug & play but I'm not certain about which ones. You can use that connection to download Broadcom software then disable and remove the USB device.  It is possible to have more than 1 wireless device.  When I have 2 functioning wireless devices and set up a network connection using Network Manager, NM will let me choose  which wifi adapter I want to use for that connection.  I hope this makes sense to you.

---

