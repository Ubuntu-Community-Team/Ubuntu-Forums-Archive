---
title: "Sharing PC-Card Internet          with      ethernet"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by photonian on 2009-02-15
CDMA access and Sharing it with home network on Intrepid
I connect to the Internet using CDMA (Verizon Mobile Service)and want to share my internet connection via eth0 (local home network).
Every time I have an Internet connection through CDMA (ppp0) then plug the network cable in (eth0), the system (**_Ubuntu Intrepid_**) starts looking to eth0 for the Internet and ignores my ppp0 connection.
After this I no longer can get on the internet, because although ppp0 is still up the system will only look at eth0 for the Internet.

I can unplug the ethernet(eth0) then the system will turn back to my already on-line ppp0(CDMA) and give me access to the internet, but then of course I can't share my internet connection with my home network.

**[CENTER]I need to share my CDMA _*(ppp0) internet connection*_ with my Home Network (eth0)[/CENTER]**


**Please** HELP!

P.S.
In Hardy I Used:

   1. Network Manager for eth0
   2. gnome-ppp for ppp0
   3. And Firestarter for DHCP and Sharing from ppp0 to eth0


But this **doesn't work in Intrepid**

And this didn't work ether ([http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html]("http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html")).

My Network Configuration Info is attached

---

