---
title: "How to make ad-hoc / bridge to raspberry pi"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by Paul_Jewell on 2013-10-04
Hello, I have tried looking over and testing extensive resources before coming here to post about this. I have a thinkpad T60 and a raspberry pi. I would like to make the two devices connect directly to each other wirelessly so that I can ssh to the pi at college. (the college has wifi but the subnets are weird and I am sure that would be trouble.) I have a realtek/alfa AWUS036H for use with the pi and the lspci for the thinkpad is listed below. Connected to the ethernet port for internet, the thinkpad has no router behind it. (wifi bridge) It would be nice to get internet to the pi, but its only really mandatory that I get the ad-hoc type connection between the two. Trying to switch the Alfa device to ad-hoc mode threw a not supported error and connecting by switching ubuntu network-manager to infrastructure mode connected but would not pull a dhcp address or work with a reasonable static one. 

thinkpad internal wireless:

```
Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)	Subsystem: Intel Corporation Device 1010
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

```

any ideas would be appreciated.

---

### Post by Paul_Jewell on 2013-10-06
Ok, Let me try to explain this a lot better because that last post was rushed and horrible. 

I would like to maintain wireless connections with a raspberry pi directly with a laptop without any kind of router. The purpose of this is to upload and run files on the pi through ftp/ssh. I already have the ssh and ftp servers working correctly through a regular network with a router, but other things I have tried so far have failed. For example, forgetting the wireless part, I tried just taking an ethernet cable between the pi and the laptop (modern laptop / auto crossover). Suggestions online pointed to setting both computers to a static ip in the same subnet. (laptop 192.168.2.1, pi 192.168.2.2) Doing this did not seem to work. From either machine I could ping and number in the subnet and it acted like it was working. (for example pinging 192.168.2.44 said it got replies) I could not ssh or ftp into the pi. So I am that much of a network noob where I can not even set that up correctly. 

Anyway, the end goal is to use the direct connection wirelessly. Neither the onboard wireless of the laptop or the usb ALFA wireless device I have seem to support "AP" mode (though I don't understand why this should be a limitation), but I also own a ASUS Wl-330gE which has an AP mode. (this is a wifi bridge device though so it might aadd an ip address in the middle - not sure how this would effect things) Believe it or not I have tried this for many hours already but no luck so far, so I came here wondering if anyone has any ideas. 

-I don't care if the pi or the laptop actually broadcasts the AP, just as long as the laptop can SSH to the pi. 
-the laptop is ubuntu 12.04, the pi is debian (minimal wheezy)

Thank you very much and have an awesome day.

---

### Post by Paul_Jewell on 2013-10-06
bump

---

