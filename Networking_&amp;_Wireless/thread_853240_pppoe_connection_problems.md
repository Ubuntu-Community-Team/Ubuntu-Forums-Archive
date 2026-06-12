---
title: "pppoe connection problems"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by Velvet Ghost on 2008-07-08
I have freshly installed Ubuntu. I have a ADSL modem connected over an ethernet port. I have configured the nm-applet that is loaded by default by enabling the 'point to point connection', setting connection type to PPPoE, and ethernet interface to eth0, and supplying my ISP username and password. I have also enabled the options 1) retry if the connection breaks or fails to start 2) use the internet service provider nameservers and 3) set modem as default route to internet. Using this setup, I am able to connect to the internet. However, I have several problems.

1) When I first start up my computer, I have to go to 'click on nm-applet icon' -> Dial up connections -> disconnect from ppp0 via modem and THEN click on 'connect to ppp0 via modem' to start the connection. If I directly click on the second choice, no connection is made. This is obviously counterintuitive and inconvenient.

2) Connection is abruptly terminated every now and then, especially when I'm not actually browsing or downloading for some time. Once the connection is terminated, reconnecting does not work. The only way I've been able to get the connection back is by restarting the computer and following the procedure in 1) above.

Also, does anybody know how to schedule the connection so that it will automatically startup everyday at a predefined time?

I could really use some help. Thanks in advance.

---

### Post by superprash2003 on 2008-07-08
i think you could use cron for this.. go to the terminal and type crontab -e and add the following line

# m h  dom mon dow   command
15 8 * * *       pon dsl-provider

in this case it would connect everyday at 8:15am in the morning.. so you could tweak accordingly

---

### Post by Velvet Ghost on 2008-07-08
Ok, I solved my problems myself. It seems that the ethernet card was not properly fitted into the motherboard! Thanks for the scheduling help superprash2003, I'll try it today. Got to get it to wake up at 2 AM!

---

