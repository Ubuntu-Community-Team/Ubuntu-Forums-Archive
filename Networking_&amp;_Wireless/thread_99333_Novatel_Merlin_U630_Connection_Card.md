---
title: "Novatel Merlin U630 Connection Card"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by AndreSchaaf on 2005-12-05
Good day. I have bought me a connection card from Vodafone (Novatel Merlin U630 Connection Card). I have installed Kubuntu 5.10. I have tried to find the card. On the linux i haven´t internet. The howtot´s don´t working on my laptop. I can´t find the card. Have anybody expirience with this card. (My laptop has 2,0 GHZ, Pcmcia, USB 2.0, wlan,lan).

With best regards
 Andre Schaaf

---

### Post by mips on 2005-12-06
Google "ubuntu Merlin U630" and "Linux Merlin U630"

Sprechen sie Deutch ?
[http://www.onlinekosten.de/forum/archive/index.php/t-59905.html](http://www.onlinekosten.de/forum/archive/index.php/t-59905.html)

[http://www.linux.org.za/Lists-Archives/glug-tech-0509/msg00049.html](http://www.linux.org.za/Lists-Archives/glug-tech-0509/msg00049.html)
[http://mybroadband.co.za/vb/showthread.php?t=31846](http://mybroadband.co.za/vb/showthread.php?t=31846)
[http://www.mybroadband.co.za/vb/archive/index.php/t-20487.html](http://www.mybroadband.co.za/vb/archive/index.php/t-20487.html)
[http://openwrt.org/logs/openwrt.log.20051116](http://openwrt.org/logs/openwrt.log.20051116)
[http://mybroadband.co.za/vb/showthread.php?t=19530](http://mybroadband.co.za/vb/showthread.php?t=19530)

If you do get it to work please come back here with the steps to make it work.

---

### Post by erk on 2005-12-18
Any luck with the Novatel Merlin U630 card? I have just ordered one, which hasn't arrived yet, and I would love to run it with Ubuntu.

---

### Post by arthur on 2006-05-12
I am probably getting that card in a few days.
No luck yet anybody?

---

### Post by arthur on 2006-05-24
Well, I finally bought it last week. Currently forcing me to use Windows, though :???:

---

### Post by bvg on 2006-06-26
hello,

There is or not a solution for this problem?
I have a Merlin U630 and the dist. is Ubuntu 6.06.

Thanks :)

---

### Post by mips on 2006-06-26
[http://ubuntuforums.org/showthread.php?t=203342](http://ubuntuforums.org/showthread.php?t=203342)
[http://ubuntuforums.org/showthread.php?t=136693](http://ubuntuforums.org/showthread.php?t=136693)
[http://ubuntuforums.org/showthread.php?t=121195](http://ubuntuforums.org/showthread.php?t=121195)
[http://ubuntuforums.org/showthread.php?t=95019](http://ubuntuforums.org/showthread.php?t=95019)
[http://www.pharscape.org/](http://www.pharscape.org/)
[http://www.orthodox.org.za/CommunityResources/vodaphone3g.html](http://www.orthodox.org.za/CommunityResources/vodaphone3g.html)


Maybe there is something usefull in the above links as there are reports & guides. The Novatel card even works in BSD.

---

### Post by bvg on 2006-06-26
[QUOTE=mips][http://ubuntuforums.org/showthread.php?t=203342](http://ubuntuforums.org/showthread.php?t=203342)
[http://ubuntuforums.org/showthread.php?t=136693](http://ubuntuforums.org/showthread.php?t=136693)
[http://ubuntuforums.org/showthread.php?t=121195](http://ubuntuforums.org/showthread.php?t=121195)
[http://ubuntuforums.org/showthread.php?t=95019](http://ubuntuforums.org/showthread.php?t=95019)
[http://www.pharscape.org/](http://www.pharscape.org/)
[http://www.orthodox.org.za/CommunityResources/vodaphone3g.html](http://www.orthodox.org.za/CommunityResources/vodaphone3g.html)


Maybe there is something usefull in the above links as there are reports & guides. The Novatel card even works in BSD.[/QUOTE]
I figure it out :)
But there's a problem, I can't ping anything :(
I already check the DNS and everything is ok!
Sugestions?

************TRACE***************
Jun 26 22:37:47 BVG pppd[31156]: pppd 2.4.4b1 started by root, uid 0
Jun 26 22:37:48 BVG chat[31167]: timeout set to 60 seconds
Jun 26 22:37:48 BVG chat[31167]: abort on (ERROR)
Jun 26 22:37:48 BVG chat[31167]: abort on (BUSY)
Jun 26 22:37:48 BVG chat[31167]: abort on (NO CARRIER)
Jun 26 22:37:48 BVG chat[31167]: abort on (NO DIALTONE)
Jun 26 22:37:48 BVG chat[31167]: send (ATH^M)
Jun 26 22:37:48 BVG chat[31167]: expect (OK)
Jun 26 22:37:48 BVG chat[31167]: ATH^M^M
Jun 26 22:37:48 BVG chat[31167]: OK
Jun 26 22:37:48 BVG chat[31167]:  -- got it
Jun 26 22:37:48 BVG chat[31167]: send (ATZ^M)
Jun 26 22:37:48 BVG chat[31167]: expect (OK)
Jun 26 22:37:48 BVG chat[31167]: ^M
Jun 26 22:37:48 BVG chat[31167]: ATZ^M^M
Jun 26 22:37:48 BVG chat[31167]: OK
Jun 26 22:37:48 BVG chat[31167]:  -- got it
Jun 26 22:37:48 BVG chat[31167]: send (ATE1^M)
Jun 26 22:37:48 BVG chat[31167]: expect (OK)
Jun 26 22:37:48 BVG chat[31167]: ^M
Jun 26 22:37:48 BVG chat[31167]: ATE1^M^M
Jun 26 22:37:48 BVG chat[31167]: OK
Jun 26 22:37:48 BVG chat[31167]:  -- got it
Jun 26 22:37:48 BVG chat[31167]: send (AT$NWRAT=0,2^M)
Jun 26 22:37:48 BVG chat[31167]: expect (OK)
Jun 26 22:37:48 BVG chat[31167]: ^M
Jun 26 22:37:48 BVG chat[31167]: AT$NWRAT=0,2^M^M
Jun 26 22:37:48 BVG chat[31167]: OK
Jun 26 22:37:48 BVG chat[31167]:  -- got it
Jun 26 22:37:48 BVG chat[31167]: send (AT+COPS=0,0,"Optimus Telecomu"^M)
Jun 26 22:37:49 BVG chat[31167]: expect (OK)
Jun 26 22:37:49 BVG chat[31167]: ^M
Jun 26 22:37:49 BVG chat[31167]: AT+COPS=0,0,"Optimus Telecomu"^M^M
Jun 26 22:37:49 BVG chat[31167]: OK
Jun 26 22:37:49 BVG chat[31167]:  -- got it
Jun 26 22:37:49 BVG chat[31167]: send (AT+CGDCONT=1,"IP","myconnection","0.0.0.0",0,0^M)
Jun 26 22:37:49 BVG chat[31167]: expect (OK)
Jun 26 22:37:49 BVG chat[31167]: ^M
Jun 26 22:37:49 BVG chat[31167]: AT+CGDCONT=1,"IP","myconnection","0.0.0.0",0,0^M^M
Jun 26 22:37:49 BVG chat[31167]: OK
Jun 26 22:37:49 BVG chat[31167]:  -- got it
Jun 26 22:37:49 BVG chat[31167]: send (AT+CGEQREQ=1,4,0,0,,,2,1500,"0E0","0E0",3,,0^M)
Jun 26 22:37:50 BVG chat[31167]: expect (OK)
Jun 26 22:37:50 BVG chat[31167]: ^M
Jun 26 22:37:50 BVG chat[31167]: AT+CGEQREQ=1,4,0,0,,,2,1500,"0E0","0E0",3,,0^M^M
Jun 26 22:37:50 BVG chat[31167]: OK
Jun 26 22:37:50 BVG chat[31167]:  -- got it
Jun 26 22:37:50 BVG chat[31167]: send (AT+CGEQMIN=1,4,0,0,0,0,2,1500,"0E0","0E0",3,0,0^M)
Jun 26 22:37:50 BVG chat[31167]: expect (OK)
Jun 26 22:37:50 BVG chat[31167]: ^M
Jun 26 22:37:51 BVG chat[31167]: AT+CGEQMIN=1,4,0,0,0,0,2,1500,"0E0","0E0",3,0,0^M^MJun 26 22:37:51 BVG chat[31167]: OK
Jun 26 22:37:51 BVG chat[31167]:  -- got it
Jun 26 22:37:51 BVG chat[31167]: send (ATDT*99#^M)
Jun 26 22:37:51 BVG chat[31167]: timeout set to 75 seconds
Jun 26 22:37:51 BVG chat[31167]: expect (CONNECT)
Jun 26 22:37:51 BVG chat[31167]: ^M
Jun 26 22:37:51 BVG chat[31167]: ATDT*99#^M^M
Jun 26 22:37:51 BVG chat[31167]: CONNECT
Jun 26 22:37:51 BVG chat[31167]:  -- got it
Jun 26 22:37:51 BVG pppd[31156]: Serial connection established.
Jun 26 22:37:51 BVG pppd[31156]: Using interface ppp0
Jun 26 22:37:51 BVG pppd[31156]: Connect: ppp0 <--> /dev/modem
Jun 26 22:37:52 BVG pppd[31156]: PAP authentication succeeded
Jun 26 22:37:57 BVG pppd[31156]: local  IP address 62.169.97.50
Jun 26 22:37:57 BVG pppd[31156]: remote IP address 62.169.67.114
Jun 26 22:37:58 BVG pppd[31156]: Connect time 0.1 minutes.
Jun 26 22:37:58 BVG pppd[31156]: Sent 0 bytes, received 10 bytes.
Jun 26 22:37:58 BVG pppd[31156]: local  IP address 62.169.97.50
Jun 26 22:37:58 BVG pppd[31156]: remote IP address 62.169.67.114
Jun 26 22:47:32 BVG pppd[31156]: Modem hangup
Jun 26 22:47:32 BVG kernel: [4407681.026000] pccard: card ejected from slot 0
Jun 26 22:47:32 BVG pppd[31156]: Connect time 9.6 minutes.
Jun 26 22:47:32 BVG pppd[31156]: Sent 1008 bytes, received 1787 bytes.
Jun 26 22:47:32 BVG pppd[31156]: Connection terminated.
Jun 26 22:47:32 BVG pppd[31156]: Exit.
************/TRACE***************

---

### Post by mips on 2006-06-27
When you say you can't ping anything do you mean host names & IP addresses ???

Can you ping the remote IP address 62.169.67.114 ? Just double check as this IP address might not be the same with every session.

---

### Post by bvg on 2006-07-03
Everything works now :)
But I have a 'little' problem, my download speed is low, above 13kB/s, in windows I can reach 40kB/s, in the same place.
I don't know what do!

Thanks...

---

### Post by xerife on 2006-07-04
[QUOTE=bvg]Everything works now :)
But I have a 'little' problem, my download speed is low, above 13kB/s, in windows I can reach 40kB/s, in the same place.
I don't know what do!

Thanks...[/QUOTE]
Hello BVG, if you've the solution, can you post it to me? and to others!!
I´d apreciate, thanks.

---

### Post by mips on 2006-07-05
[QUOTE=bvg]Everything works now :)
But I have a 'little' problem, my download speed is low, above 13kB/s, in windows I can reach 40kB/s, in the same place.
I don't know what do!

Thanks...[/QUOTE]

What are you using to download stuff with. What speed do you get with a download manager like D4X or similair ?

How did you fix your problem so others here can benefit from your experience. What link did you follow and how did you get ping working.

---

### Post by arthur on 2006-07-06
Could you provide the details to make it work, BVG?
Cheers!

---

### Post by mips on 2006-07-08
Maybe BVG does not look at the thread anymore seeing his problem is sorted out.

Maybe PM/Email BVG and ask for a response.

---

### Post by arthur on 2006-07-09
Cheers, Mips, will do that ;)

---

