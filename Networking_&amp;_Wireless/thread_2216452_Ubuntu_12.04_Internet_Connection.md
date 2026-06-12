---
title: "Ubuntu 12.04 Internet Connection"
date: 2014-04-12
forum: Networking &amp; Wireless
---

### Post by kiran_majumder on 2014-04-12
Hi All, I have recently conigured dual boot(Win 7 & Ubuntu12.04) in my PC. I have router for my cable net connection. In that router I have manually conigured my internet settings, and it is working fine for Win 7. But I am unable to connect from Ubuntu[IMG]http://srv.xossip.com/images/smilies/confused.gif[/IMG][IMG]http://srv.xossip.com/images/smilies/confused.gif[/IMG] . I am using Intel DB85FL 4th generation motherboard. Is there any compatibility problem with my Mother board?  Any help appreciated.

---

### Post by Ubi_one_2014 on 2014-04-12
how did you configure the router?

---

### Post by kiran_majumder on 2014-04-12
Thanks for your reply. I am using Dlink dir600L router. I did the configuration from windows and it is working fine.

---

### Post by Ubi_one_2014 on 2014-04-13
so you using the same hardware on Linux and on windows, to get online?
wireless or wired?

---

### Post by kiran_majumder on 2014-04-13
Yes, I am using the same hardware for Linux and Windows, with wired network. I have done this with my previous motherboard also. 
But right now after reconfiguration of my PC's hardware, Ubuntu can not able to find out Mac address of my system. Today I have tried my net connection in one of my friend's laptop with Ubuntu and it is working fine. Is there any way to download network adapter driver for a particular motherboard?
I am using Intel DB85FL MBoard.
> **Ubi_one_2014 said:**
> so you using the same hardware on Linux and on windows, to get online?
wireless or wired?

---

### Post by Bashing-om on 2014-04-13
kiran_majumder; Hi !

I'll do what I can to nudge this along.
Isolate to a config situation, can you ping your router ?
```

route -n

```
in that output is the gateway address - the IP under "Gateway".
Can you ping that address ?
```

ping -c3 192.168.0.1

```
where '192.168.0.1' is a common router IP, yours may be different.
That result will give the indication of where next to look.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by kiran_majumder on 2014-04-26
[COLOR=#000000][FONT=verdana]Thanks all, for your valuable response. Ultimately Ubuntu has released the lan driver for Intel DB85FL mother board in ubuntu14.04...[/FONT][/COLOR][IMG]http://srv.xossip.com/images/smilies/smile.gif[/IMG][COLOR=#000000][FONT=verdana] [/FONT][/COLOR][IMG]http://srv.xossip.com/images/smilies/smile.gif[/IMG][COLOR=#000000][FONT=verdana] [/FONT][/COLOR]

---

