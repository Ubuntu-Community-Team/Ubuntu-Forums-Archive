---
title: "internet problems"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by HelterSkelter1989 on 2008-10-14
first off my wireless internet will not work, the network will not even show up. i was told i could fix this problem by downloading certain drivers. however when i plug in the ethernet cable to download the drivers and install updates, it won't connect to the wired connection either. it says the connection is secured and asks for a name and password and such things. the only problem is i'm connecting directly from my cable modem which is NOT secured and has NO name or password or any such things. why does it ask for these things and what can i do to access the internet?

---

### Post by HelterSkelter1989 on 2008-10-15
is there a certain something i need to do to connect? why won't it let me connect with an ethernet cable?

---

### Post by louistan3 on 2008-10-15
if you connect your ethernet cable, do you get an IP? turn off your wireless just to be sure.

---

### Post by superprash2003 on 2008-10-15
do you have a cable modem?? in windows xp do you use a dialer to connect.. post output of ifconfig from your terminal

---

### Post by stankopp on 2008-10-15
I have just installed 8.10 (was running 8.04 just fine).  I can not get the Network Applet Manager (0.7.0) to configure my IP4 information.  I want to use a static IP (we do not do DHCP here at work) with the following information:
IP address: 1.1.8.52
Subnet Mask: 255.0.0.0
Router       1.1.1.88
DNS          1.1.1.99 and 1.1.1.199
(the exact same information that I had in 8.04)

When I enter that information and click the OK button, the subnet mask changes to 8 and the IP address to 0.0.0.0.  In that state, I can connect to the local network, but can not connect to the internet.

I have tried editing the /etc/dhcp3/dhclient.conf file as suggested in the sticky, and entering all of the data there including the pre-disposition of the DNS name server, but that has no effect. 

What do I need to do to make this work?

---

### Post by HelterSkelter1989 on 2008-10-15
it gets nothing but the mac address. it is connected correctly, i have my wireless turned off before i even booted up ubuntu, and my internet is working. i cannot update my ubuntu since i have never been able to connect with it so please don't suggest updating unless there is an offline way of diong so lawl.

---

### Post by stankopp on 2008-10-21
I have given up on 8.10 beta.

---

### Post by stankopp on 2008-10-31
I have just installed the release of 8.10.  I see that the IP addressing problems persist.  What is the point of beta testing if the problems don't get fixed?

8.10 is pretty much useless as it sits.

---

