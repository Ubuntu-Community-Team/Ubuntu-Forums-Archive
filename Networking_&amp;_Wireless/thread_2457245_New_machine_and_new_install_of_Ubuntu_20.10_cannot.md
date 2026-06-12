---
title: "New machine and new install of Ubuntu 20.10 cannot ping printer"
date: 2021-01-28
forum: Networking &amp; Wireless
---

### Post by jgwphd on 2021-01-28
I have a new Dell Inspirion 14 5000 laptop. I just finished dual booting it with windows and installed Ubuntu 20.10. Everything works fine until I tried installing my home printer using hplip 3.20.11 and got the message  hplip "cannot detect the printer" even when using manual discovery with the printer IP address (which is 192.168.1.3). 

The new laptop is connected on the same LAN as the printer using WiFi with an IP address of 192.168.1.11 (802.11 is the only connectivity option since their is no Ethernet connection on the new laptop). I can browse the web with no issues. So in the browser I tried http:\\192.168.1.3 which timed out. Then in a terminal I tried "ping 192.168.1.3" which after a few minutes I cancelled with ctrl-c and got "128 packets transmitted, 0 received,100% packet loss..." Additional information: It seems that ** I can't ping anything on my LAN **including the router at 192.168.1.1 I always get 100% packet loss. My network proxy is set to off (disabled). But I can ping 8.8.8.8 successfully with NO packet loss. I also rebooted the NetGear AC1900 wireless router with no effect on the problem! 

This new laptop is in a room with the printer and two other Ubuntu machines **running 20.10**. One machine is Ethernet connected and the other is WiFi connected just like the new machine. Both work fine and can ping the printer address 192.168.1.3. The default route and DNS are all the same for all three machines. I was able to install the printer on windows on the new dual booted laptop (same machine with Ubuntu that can't ping the printer) and print a test page. I can't ping the other 2 machines (desktop and other laptop on my LAN) from my new laptop, but they can ping each other successfully. Neither of the existing machines can ping the new laptop (they get 100% packet loss). I can ping myself successfully (if that piece of info is useful).

I would greatly appreciate any suggestions on how to proceed. Many thanks!

---

### Post by jgwphd on 2021-01-28
In my home my NetGear AC1900 Nighthawk R7000 router is configured with 4 wireless LANs
 
- one at 2.4 Ghz
- one at 5Ghz
- a guest network at 2.4 Ghz
- a guest network at 5 Ghz

When I moved my wireless LAN connection to the network at 2.4 Ghz everything started working (I was on the 5 Ghz guest network before), all pings now work correctly and I successfully installed the printer. Anyone have any idea what I am doing wrong????  If no one knows I'll just close this in a day or two. I am just happy to have everything working but I would sure like to know what I did wrong so I can avoid this issue in the future. I am thinking there are restrictions on a "guest" network that prevent guests from using any equipment on the LAN except internet access. If true, then boy did I go down the tubes on this one!!!! Thanks!

---

### Post by CelticWarrior on 2021-01-28
Guest networks, by definition, are isolated.

---

