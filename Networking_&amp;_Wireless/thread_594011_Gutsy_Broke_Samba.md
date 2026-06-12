---
title: "Gutsy Broke Samba"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by ReverendJ1 on 2007-10-27
Since I upgraded to Gusty last week my Samba server has not been working correctly. I have read a few posts but still no luck. I seem to have a slightly different problem then everyone else.
If I put in my Ubuntu box's name in an XP machine I can see all of my Samba shares. When I try to open any of them though I get an error "\\ubuntubox\share refers to a location that is unavailable." When I put in the ip address instead, I can still connect to the shares just fine. 
So "\\ubuntubox\share" Does not work, but "\\192.168.0.5\share" does.
Does anybody know of any reason why I can see my shares but not open them using the network name?

---

### Post by OldGaf on 2007-10-29
I have the same problem. I have a Feisty printer server using Samba to share printer with Win / Linux LAN. On my main PC, everything was easy with Feisty. Did a clean install of Gusty AMD64 and no samba shares are detected, no printer available. I have the same samba config in gusty I was using in Feisty..... no network.

---

### Post by ReverendJ1 on 2007-10-29
I noticed over the weekend that everything was working just peachy on another XP machine on the network. I could put in "\\ubuntubox\share\" and it would pop right up. I decided to do a DNS flush on the computer that wasn't working, but it didn't do anything. Then yesterday it stopped working on the XP machine that was working Saturday. Argh.

---

### Post by sewpafly on 2008-01-20
Did you ever find the cause of this problem?  I finally upgraded to gutsy and got the same problem...

---

### Post by ReverendJ1 on 2008-01-29
Sorry for the late reply, I haven't been back on here in a while. If I remember correctly I think it just sort of fixed itself. I think it must have been some update or something. But again, I am not 100% sure.

---

### Post by sewpafly on 2008-01-29
> **ReverendJ1 said:**
> Sorry for the late reply, I haven't been back on here in a while. If I remember correctly I think it just sort of fixed itself. I think it must have been some update or something. But again, I am not 100% sure.
That's what happened to me.  I rebooted all the computers on the network and it seemed to work.

---

