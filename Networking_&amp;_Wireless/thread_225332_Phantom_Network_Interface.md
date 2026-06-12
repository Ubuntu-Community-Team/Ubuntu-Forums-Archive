---
title: "Phantom Network Interface"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by diamond on 2006-07-29
When I installed Dapper on my Inspiron 600m, I had (as do many) a little trouble getting wireless networking to work. When I first installed ndiswrapper, it set up my wireless adapter as eth1 and it didn't work. After much messing around, getting the newest ndiswrapper, and finally blacklisting the bcm43xx module, I fixed the problem. Wireless is now working just fine on an interface called wlan0.

However, even though the eth1 interface seems to be  gone, there's still some vestigial remnant of it. Whenever I start up, the "Network Connection" applet on the top panel shows an error, because it's trying to show the status for eth1 -- which, of course, no longer exists. I have to manually switch it over to wlan0 before it shows a healthy connection and the wireless signal strength bar.

This is not a critical problem, because it doesn't actually interfere with my connection. But it is annoying. Somewhere, some configuration file is telling this thing to get connection status from eth1 by default (it even happens when I resume from hibernate), instead of wlan0. Any idea where I can look to change this?

---

### Post by diamond on 2006-07-29
Never mind. Problem solved.

If anyone else has the same problem, the solution is simple. In my /etc/network/interfaces file, the very last line was "auto eth1". All I had to do was delete that, because the previous block was the setup of wlan0, which included the command "auto wlan0".

---

