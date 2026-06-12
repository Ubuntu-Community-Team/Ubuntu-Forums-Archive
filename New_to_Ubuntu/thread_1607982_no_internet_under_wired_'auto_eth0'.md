---
title: "no internet under wired 'auto eth0'"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by 1905krishnan on 2010-10-28
hallo Ubuntu experts,

I am new to ubuntu. i have India BSNL hUAWEI WA1003A modem cum router, wired connection to desktop(windows xp32 bit) and wifi to laptop(windows 7 64 bit). Recently i created unallocated diskspace of 16 GB in desktop and installed the downloaded desktop ubuntu 10.10 version. **Network status says 'wired auto eth0 connected' and the OS neatly downloading all the updates. But i could not browse internet.** Ping fetched nothing. under winxp and win7 internet working fine. But under Ubuntu i could not browse. I tried reinstalling Ubuntu in vain.

After installing Ubuntu i was elated that i fulfilled my long cherished dream of using open source OS. I tried all the methods (understandable to my limited knowledge) to configure network. But i got frustrated.

Kindly help. I am very grateful sir.

krishnan

---

### Post by Perseverance on 2010-10-28
If you are using mozilla , there is a common issue with IPv6 settings. Also getting no ping suggests bad DNS choice. So once again the solution ( I have quite get use to writing this):
In firefox about:config and find network.dns.disableIPv6 and set it to true if it is not already set. If than you are able to connect to some web page go to [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/). If dont go to your other OS and do the same. Take the first calculated  DNS and place it in Here : Right click network icon -> Edit Connections -> At auto eth0 click edit->IPv4 -> DNS Server. At the tab IPv6 make sure it is set to Ignore.

Hope That helps

---

### Post by 1905krishnan on 2010-10-28
ho, thank you perseverance, i didn't expect such quick reply. i will try what you said and inform you.

---

### Post by 1905krishnan on 2010-10-28
:PGreat perseverance,
that works. In firefox i simply disable ipv6 and it rocks. Once again _[COLOR=DarkRed]**thank you**[/COLOR]_ very much.:popcorn:

---

### Post by Perseverance on 2010-10-29
You Are Welcome :) Mark The Thread as SOLVED please :P

---

### Post by Perseverance on 2010-10-29
The explanation : 
The way your connection is behaving suggest bad dns server ( with either slow response time or Only IPv6 settings enabled).To speed up your firefox you need to disable IPv6 usage there.

Hope that helps

---

