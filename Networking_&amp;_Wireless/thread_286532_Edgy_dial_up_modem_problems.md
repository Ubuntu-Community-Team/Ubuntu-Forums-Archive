---
title: "Edgy dial up modem problems"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by mcsix on 2006-10-27
Just installed Edgy. I tried to upgrade first but had nothing but problems so I changed to a clean install. 
I am using an external trendnet modem. Worked flawlessly in dapper. I did not really even have to configure anything. It just worked. Now with edgy, the modem is not even detected. I have messed around with pppconfig. Nothing seems to work. What do I have to do to get edgy to see the modem?
Any help is greatly appreciated. I don't want to have to go back to  Dapper but it is looking like I may have to.
Thanks.
Brian

---

### Post by mcsix on 2006-10-28
Okay, I got it it find my modem using wvdialconf. Then when I use wvdial I can connect to my isp. At least the modem appears to be connected. The lights are lit up on it. How do I tell if it is actually working? The problem now is that when I am connected no services are using the connection. I cannot actually access the internet using the connection. What do I need to do for the connection to be used?

---

### Post by maxter on 2006-11-06
i've got the same problem, and solved it using wvdial...
did you configured wvdial using wvdialconf?
did you edited the /etc/wvdial.conf accornding to your isp data?
did you removed the ; from /etc/wvdial.conf's isp data?
did you used pon.wvdial to activate the connection? i reported a lot of problem activating the connection using only 'wvdial'.

Max

---

