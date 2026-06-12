---
title: "Can't access MSN"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by dingorunner on 2007-06-27
Hello, I've been using Ubuntu Feisty for a couple of months and everything was going great until eventually Gaim stopped being able to connect to MSN and I realised that I have the same issue with Firefox and [http://www.hotmail.com](http://www.hotmail.com). At the beginning I was able to login to MSN and check my hotmail from Firefox but now I can't. but I'm able to login to MSN from Meebo. 
I have XP in this computer (because I haven't being able to configure any VOIP program to support my local VOIP provider), well the funny thing is that I can access Hotmail using Firefox in XP and Windows Live Messenger works just fine. 
I hope you guys could help me fixing this issue.

---

### Post by Threbus5 on 2007-06-28
Hi,

Could this represent a domain name resolution issue?

When you connect to MSN or hotmail using the other OS's obtain the MSN/hotmail IP address and then try to browse to the IP addresses via the Feisty machine.

Try logging into another web site then clearing browser cache - if the cache contains an "inability to connect page" for MSN or hotmail then it will keep presenting that instead of attempting to connect.

Best wishes

---

### Post by dingorunner on 2007-06-28
Hello. Well could you please tell me how do I get those  IP addresses and how to browse those IP addresses once I have them. I guess I didn't make myself clear: I can access [http://www.msn.com](http://www.msn.com) but I can't  log in to MSN Messenger using Pidgin (Meebo works) and [http://www.hotmail.com](http://www.hotmail.com) doesn't even start loading.

Recently I found out that there are other websites that firefox doesn't even load:
[http://www.wordreference.com](http://www.wordreference.com)
[http://www.learnenglish.org](http://www.learnenglish.org)

When I say the website doesn't load I mean that firefox's status bar remains blank.

---

### Post by Austin_KW on 2007-06-28
That could be a path mtu problem, do you also have problems getting to secure (https) sites.
You might try reducing the mtu on your ethernet interface

sudo ifconfig eth0 mtu 1400

---

### Post by dingorunner on 2007-06-28
I typed 'sudo ifconfig eth0 mtu 1400' on my terminal and it asked for my password but nothing visible happened. I restarted firefox and I'm still not able to visit those webs.

---

### Post by dingorunner on 2007-06-29
hello, I have new data for regarding this issue; 
Another unaccessible web; [http://www.dattebayo.com](http://www.dattebayo.com). I'm in ubuntu using LiveCD; guess what,. same exact problems; No MSN, no Hotmail. and no other webs I've already 
mentioned.
When I try to visit one of those websites firefox 'tries' opening it but eventually it goes;

The connection has timed out

The server at [www.hotmail.com](www.hotmail.com) is taking too long to respond.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments. (It's been 3 days)

    *   If you are unable to load any pages, check your computer's network
          connection. (I can load a lot of other pages)

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web. (I don't use proxy and I already tried                                  'sudo firestarter -p' and besides, this issue started before I even installed firestarter)



 
I hope that info was helpful.

---

