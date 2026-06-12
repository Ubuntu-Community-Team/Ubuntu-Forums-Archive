---
title: "[SOLVED] Internet stopped working."
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by diwas on 2008-07-16
I have TP link TD-8817 ADSL 2/2+ Router connected via LAN into my system. Actually the internet was 

workin all right without any problem whatsoever. But azureus wasnt working due to the port porblem 

([http://ubuntuforums.org/showthread.php?t=855503&page=2](http://ubuntuforums.org/showthread.php?t=855503&page=2)). I poted the thread and then i was 

instructed toward port forwarding. I read about them but couldnt do anythin... 

Read the extract of the post i made. This is after i log in to 192.168.1.1. The bridge mode and all 

are under "Interface Setup" tab.

Well, it was working all fine till the day i changed the bridge mode to PPPoA/PPPoE and saved 

it...went to NAT and saw (the screenshot is already uploaded). Then again changed the PPPoA/PPPoE to 

bridge mode...not sure what to do and saved it again. The internet was working fine till then. But 

when i rebooted the system...it stopped working.
I havent changed anythin, thus im very suprised as what could be the problem. Its working fine in XP, 

wid the same router of course.


diwas@diwas-desktop:~$ plog
Jul 14 18:43:05 diwas-desktop pppd[5841]: Plugin rp-pppoe.so loaded.
Jul 14 18:43:05 diwas-desktop pppd[5843]: pppd 2.4.4 started by root, uid 0
Jul 14 18:43:05 diwas-desktop pppd[5843]: PPP session is 6044
Jul 14 18:43:05 diwas-desktop pppd[5843]: Using interface ppp1
Jul 14 18:43:05 diwas-desktop pppd[5843]: Connect: ppp1 <--> eth0
Jul 14 18:43:05 diwas-desktop pppd[5843]: CHAP authentication failed: Account is occupied
Jul 14 18:43:05 diwas-desktop pppd[5843]: CHAP authentication failed
Jul 14 18:43:05 diwas-desktop pppd[5843]: Connection terminated.

diwas@diwas-desktop:~$ ifconfig ppp0

ppp0 Link encap:Point-to-Point Protocol

inet addr:10.1.232.172 P-t-P:10.1.0.1 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1492 Metric:1
RX packets:15 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:7584 (7.4 KB) TX bytes:749 (749.0 B)




Here's what i get in the terminal when i execute the commands.

---

### Post by diwas on 2008-07-16
Please Help

---

### Post by diwas on 2008-07-17
Well, do i need to re-install the OS for this?? I have searched through the internet but i couldnt get any help from them. Please help me.
Thank you.

---

### Post by diwas on 2008-07-19
Well now the internet works...i dont know how but it does. Day before yesterday i had pressed the "reset" button. May be that is the reason.

---

