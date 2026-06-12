---
title: "Problem with Internet Connection"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by D BRUCE on 2010-06-10
Hi all,

I am using ubuntu 9.04.I've been facing problem with internet connection through modem.
Previously I posted the same query and got the reply as below.

""Connect your computer via Ethernet cable to the broadband modem, and Ubuntu should get a connection automatically. If you find that you can't access websites, then the router isn't correctly passing DNS information - you can go to System > Preferences > Network Connection, select your Ethernet entry under Wired, click Edit and go to IPv4 Settings tab, change the method to "Automatic (DHCP) Addresses Only" and enter the following in the DNS field:
Code:208.67.220.220
Disconnect and reconnect and you'll be up and running.""

I am pretty much thankful for that suggestion.

Every thing went well after doing as above.But two days later when I started my machine and tried to connect to the internet,a message like " Wired connection is unplugged" (I am sorry I didn't remember the exact message) is displayed.Auto etho connection also failed.Later in my trials I accidentally deleted etho from the network manager's connection type list.


I am sorry if the post length is too long.

Please one help me out.


regards,
D Bruce

---

### Post by kennedyvelez on 2010-06-10
> **D BRUCE said:**
> Hi all,

I am using ubuntu 9.04.I've been facing problem with internet connection through modem.
Previously I posted the same query and got the reply as below.

""Connect your computer via Ethernet cable to the broadband modem, and Ubuntu should get a connection automatically. If you find that you can't access websites, then the router isn't correctly passing DNS information - you can go to System > Preferences > Network Connection, select your Ethernet entry under Wired, click Edit and go to IPv4 Settings tab, change the method to "Automatic (DHCP) Addresses Only" and enter the following in the DNS field:
Code:208.67.220.220
Disconnect and reconnect and you'll be up and running.""

I am pretty much thankful for that suggestion.

Every thing went well after doing as above.But two days later when I started my machine and tried to connect to the internet,a message like " Wired connection is unplugged" (I am sorry I didn't remember the exact message) is displayed.Auto etho connection also failed.Later in my trials I accidentally deleted etho from the network manager's connection type list.


I am sorry if the post length is too long.

Please one help me out.


regards,
D Bruce


Sir,

 Try using the Terminal sudo pppoeconf, then follow procedure... Enjoy... By the way, don't forget to upgrade to 10.04 LTS

---

