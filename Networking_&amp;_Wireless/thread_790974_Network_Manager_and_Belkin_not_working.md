---
title: "Network Manager and Belkin not working"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by kingair_six on 2008-05-11
Hello,

I believe this is my debut in this forum, so "Hello, World!".

I've been running xubuntu and ubuntu hardy heron for a couple of weeks now, and I must say, it's great. 

Though, xubuntu is causing me problems with the Belkin 7010 PC Card (Broadcom Chipset). I installed the b43 driver from linuxwireless.org, threw in wifi-radar and hoped for the best, since some posts suggested that might work. Now when I do "iwconfig wlan0" it recognizes the adaptor,but does not show any action.

Network Manager does not work atm, I don't know why, it used to work before I tried using this card to connect. My network is simply WEP protected, so that should not cause the problem, right? Aside from this, when I manually configure the card via Applications>System>Network or so, and set it to my wifi network, SSID and so on, it still does nothing, just says it cant retrieve an IP.

I'm kinda clueless on thisone, since I'm really just a noob with linux, so any help would be really appreciated!;)

kingair_six

---

### Post by Nesster on 2008-07-09
Hi, I have the same card (same chipset). Did you find something useful for your problem ?

I was able to connect at work with a Linksys WRT54G, version 8. 

But at home, with same laptop and router, but version 2, I can't connect. I see my adapter (7010) being associated with the SSID I setup in the config files (interfaces and/or wpasupplicant), but it can't get an IP.

---

### Post by YanH on 2008-07-12
I also have the same problem with Network Manager. The computer can recognise the card and the Network Manager can talk to the Router. Network Manager displays available wireless networks and their signal strengths. However if you actually try and connect it always fails. The authentication method is WEP. The wireless network is working correctly and other machines both Linux and Windows can connect.

---

### Post by Kevbert on 2008-07-12
Please check out this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560").  It seems to be the best one for wireless.

---

