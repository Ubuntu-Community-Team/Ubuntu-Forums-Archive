---
title: "Strange WIFI Problems"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by TimDuncan on 2007-04-14
Hi everybody, I desperately need help here. I installed Ubuntu 6.10 Edgy on my new laptop, everything works perfectly except for my wireless.
I'm running an Intel PRO/Wireless 3495 with the ipw3495 drivers. My first problem was that the wireless interface disappeared completely from the system, but I did a quick re-install of ubuntu and that fixed the problem.

The current problem I have only occured after running aircrack-ng, to see how secure my home network was. I found out my card didnt support injection at the moment so I cancelled airodump and used iwconfig to set the card's mode from monitor back to managed. 

Now it seems my wireless at home is running at about dial-up speed, which is strange because i'm running a 1.5 mbit ADSL connection, and i have an i-mac running wireless, and it's achieving full speed.

I ran a speed test on [www.speedtest.net](www.speedtest.net), and i found the problem wasn't actually the speed of the wireless, as it was getting full download speeds. The problem seems to be that it takes a LONG time to connect, or to get information from the AP.

I'm at my friends house at the moment (out in the country) and he is running a totally unsecured network, with no MAC filtering or anything, and here i cannot even get a single web page to load. I can connect to his wireless AP fine, i get 80% signal, and i can ping the AP, however i cannot get a webpage up whatsoever.

I'm resorting to running windows XP at the moment which works fine... which is strange :P

I tried to save some screen dumps but it seems windows won't read them, so i can't post them as yet. I will be able to when i get home and can plug directly in.

Does anybody have any suggestions on how to fix the speed / webpages not loading issued?? I cannot even connect to the AP firmware through firefox, it just gives me the loading symbol. 

Any ifconfig / iwconfig settings that should be changed??
Any ideas would be greatly appreciated!!!
Thank you in advance

Tim

---

### Post by TimDuncan on 2007-04-14
I found out the problem was actually the router not providing accurate DNS namespaces. To counter this, i had to manually edit resolv.conf and add in "namespace xxx.xxx.xxx.xxx" where the xxx is an online DNS server provided by my friends ISP.

It's still strange that i only get this problem in Ubuntu, and not in windows, there must be some compatibility issues with the router.

The only problem is every time i reconnect it automatically updates resolv.conf with the default 10.1.1.1 DNS namespace.

Is there any way i can override this automatic update?


Thanks!

Tim

---

