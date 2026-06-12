---
title: "Wireless problems connecting to d-link router - Help - I have to use Vista otherwise!"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by Ultra Magnus on 2007-09-02
Hi I need some help. I can't get Ubuntu to see my wireless network. I can usually connect to most networks so I don't know whether this is a problem with the router or with my configuration or what really.

My wireless card is an Intel(R) PRO/Wireless 3945ABG card built in. and it comes up as eth1.

When I type:

ifdown eth1

It says that eth1 is not properly configured

when I type 

ifup eth1

It says the device is unknown.

I have never had any problems connecting to other wireless networks and it seems to be just this router, so I thought there might be a router problem, so I updated the firmware but nothing changed.

Once, very briefly I was able to see my network on Ubuntu but when I tried to connect it became no longer visible. Ive tried using other distros to connect incase I've done something stupid and broken it in Ubuntu but I had the same problems in Knoppix and Sabayon both of which have worked in the past.

My dads XP laptop can connect fine but two vista laptops in the house occasionally have trouble. The router itseld is a D-Link DSL-G604T wireless router, has anyone had this problem before or have any idea what could be wrong?

Thanks Allot.

Jim

PS - As per my title, I have to use vista If i can't get it to work in Ubuntu, but everything is slowly breaking in vista - it doesn't even recognise my DVD drive anymore - So i'm left with having to reboot constantly into different operating systems depending on what I want to do which kind of sucks after a while.

---

### Post by Ultra Magnus on 2007-09-02
bump - I've tried following the trouble wireless trouble shooting at [https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

I got up to step 7 with no problems after adding a line into my /etc/network/interfaces file - Previously there was no entry for eth1 (my wireless card)  and ifup and ifdown works now

ifup searches for a dhcp client but says there are no offers - On the router settings page the dhcp client is enabled - I'm still unable to see the network though.

typing 
iwlist scanning
yields no results.

---

### Post by Ultra Magnus on 2007-09-03
bump - I've decided to try a usb wireless dongle (a dlink dwl-122) unfortunately i couldn't get it too see any networks from Ubuntu either - Ubuntu recognised the wifi adapter but still couldn't see any networks. 

So i installed xp on a virtual machine in vmware and installed the usb adapter in XP and got it to work no problems, so atleast I can use Linux while on the internet, although its a bit silly to run vmware just to be able to connect!

I checked the router page and on the dhclient list XP is listed as well as Ubuntu! - So my router can see me but I can't see my router!

Does anyone have any ideas how to proceed from here?

Thanks

Jim

---

### Post by meindian523 on 2007-09-03
You sure you need DHCP?Do you have a static IP address?

---

### Post by Ultra Magnus on 2007-09-03
Hi.

I have my wifi set to roaming - I have tried to set up a static ip address but It didn't work.

The DHCP client on the router is enabled but when I type: sudo dhclient eth1 - it says there are no offers.

I have tried with two wireless cards and can't see the network.

Thanks

---

### Post by meindian523 on 2007-09-03
Just saw that it's wireless.....wireless is known to have some problems in Linux in general thanx to the lack of hardware support by manufacturers.You will have to wait for someone who has more "beans" to help you out on this.In the meantime,search these forums with the keywords wireless Ubuntu --Insert version here-- I believe you will get some useful results.

---

### Post by Ultra Magnus on 2007-09-03
Hi.

Thanks for your help, this is the first real problem I have had with Ubuntu that hasn't taken 10 minutes of googling to fix - My wifi card is exactly the same as that in the systems sold by Dell with Ubuntu and it worked out of the box for my old router so I think it may be a configuration thing.

Thanks

Jim

---

### Post by meindian523 on 2007-09-03
Well,I sympathise with you and apologize that I couldn't help more.....

---

