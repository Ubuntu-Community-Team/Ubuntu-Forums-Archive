---
title: "Configuring Netgear N150 Model DGN 1000 by changing MTU"
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2014-08-29
Hi all
Recently I purchased 'Netgear N150 Model DGN 1000' from Amazon.in and tried to configure it using Netgear genie. The configuration went smooth without any hitches. But I noticed a problem and it was that some sites like google  and gmail opened but sites like Yahoo and Paypal did not. I thought that it might be due to channel interferance and changed the Chanell from 1 to 3, then to 11... No difference. I tried with other machines which run on Ubuntu(I have 3 machines one on Kubuntu, One on Lubuntu and the third one on Ubuntu Gnome), still no luck. This is when I thought of MTU (Maximum Transmission Unit). I tied the following codes from this [thread]("http://ubuntuforums.org/showthread.php?t=1376506") to know my MTU. The codes are follows which has to be entered in terminal
```
ping [COLOR="#FF0000"]ip.of.your.router[/COLOR] -c 1 -s 1400 -M do
```
```
ping [COLOR="#FF0000"]ip.of.your.router[/COLOR] -c 1 -s 1501 -M do
```

The red coloured text in the code should be replaced by your ip number of your router. In my case it was 192.168.01
I found out that my MTU was 1400 by checking. I resetted the MTU in Netgear configuration by using Netgear genie app to 1400. The app can be accessd through [www.routerlogin.net](www.routerlogin.net). You have to navigate through 'Advanced-->Setup--> WAN Setup'. See the screenshot

I tried this still no luck. Then I did one **fluke**

I configured the MTU settings in each machine to 1400 and the magic worked. In each machine I used the appropriate network manager and changed the MTU from automatic to 1400 and it WORKED[ATTACH=CONFIG]255932[/ATTACH]

---

