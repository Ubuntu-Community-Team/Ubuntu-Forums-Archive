---
title: "Wireless connection drops and doesn't reconnect"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by kbehel on 2008-02-09
I'm running Feisty with a D-Link G132 USB network adapter. I got this working using ndiswrapper (v1.52) , D-Links ver121 drivers, static routes. When I transfer a lot of data (such as streaming video) the connection will eventually drop and then not reconnect. iwconfig says that the interface is up, but then for the Access Point it says that there are none associated. ping does work, /etc/init.d/network restart doesn't bring the wireless connection back, nor does 
ifdown wlan0
ifup wlan0

It acts like the computer doesn't realize that the link is down.

I believe this is an ndiswrapper issue based off other postings ( [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/190144](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/190144)  )
but I'm not sure how to prove that.

Does anyone know how to get this working, or can they confirm that ndiswrapper has problems when there is a lot of data traveling over the network?

thanks,

Kevin

---

### Post by Bubba64 on 2008-02-09
Are you running more data then the usb can support. When I have lost my wireless usually just turning it off in the manual network configuration closing it after the processing then opening it up again and turning the wireless back on will get everything working again. This may not be an answer that works with your question.

---

### Post by kbehel on 2008-02-10
not the usb speed - usb 2.0 speed is much higher than 802.11g even in the best of wireless connection environments.

Nothing brings the connection back. /etc/init.d/networking restart nor ifdown/ifup. The problem appears to be related to either ndiswrapper or it's interaction with the 7.04 ubuntu. I know ndiswrapper has had numerous problems like this when the traffic was high. Supposedly this was fixed around or before the 1.4x versions. So I assume this is an Ubuntu specific problem.

I can make this happen when I stream video through mythtv or by transferring a lot of data over NFS. 

Kevin

---

