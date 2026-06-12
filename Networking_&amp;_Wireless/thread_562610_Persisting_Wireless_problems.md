---
title: "Persisting Wireless problems"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by devosion on 2007-09-29
I just recently installed Ubuntu, about 2 days ago, and i've been having a problem connecting to the router so I can access the internet. Im using a Linksys Wireless-G router v4 and I downloaded the windows driver available, wusbgv4, from the linksys site to use as my device driver with ndiswrapper. I have managed to successfully get ndiswrapper to identify the hardware to the driver, but strangely enough in the windows device driver window, part of the gui for ndiswrapper, it shows the device not found for the driver. After I first did this I connected to my network, my network settings are set to roaming mode with a security passcode and nothing else set. After I did this I got no connection to either the internet or router. I did not find this out immediately, but after a restart, which incidentally 
worked somewhat strangely.

Prior to restaring ubuntu I used the ndiswrapper -m command for saving my driver and device settings for start up, but at start up the connection did not work. Not even when I inputted the web key in the network window. I then made some changes by going to a manul configuration, and then back to roaming mode and for some reason I got the icon to change to that if I was connected. Problematically though I did not have a connection to either the network or the internet. I found this out when I pinged my modem and got no response. When I pinged my localhost this worked out just fine. 

Im not exactly sure what direction I should go to get this resolved by im open to all ideas right now. Thanks!

---

### Post by devosion on 2007-09-29
Please disregard. The problem is solved.

---

