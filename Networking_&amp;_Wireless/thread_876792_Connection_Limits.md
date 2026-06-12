---
title: "Connection Limits???"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Merrigan on 2008-08-01
Hi There,

I have been using Ubuntu for my desktop for some time now, and because of the speed & success of that, I converted all my Network servers to Ubuntu x86_64 installations as well.

Everything seems to be working, for the most part. I am however experiencing a slight problem on my Proxy machine.

It's a dual core Server with 2GB RAM and all the bells & Whistles. I Use squid for proxying. Everything works fine until the machine decides to randomly start timing clients out.

I have been working at this for a long time now, and don't have any other thoughts on this, except that there might be a limit on the amount of network connections Ubuntu can handle. (I know for Windows XP this is 10 connections) This makes no sense to me, as I would not put something like that on, but we all know anything is possible.

Is there anyone out there that can give me some info on this, it would be very appreciated.

Thank you!!!

---

### Post by rahmath on 2008-08-01
i didnt get you exactly. Do u mean the no of connections handled by Ubuntu at a time or no of connections handled by squid at a time?

---

### Post by Merrigan on 2008-08-01
Well,

I actually meant by Ubuntu, hadn't thought of squid, but that is also a valid thought...so let's say both...

I have noticed that when a user has been getting timeouts on squid, that the user's computer is also unable to ping the proxy server...

---

### Post by airtonix on 2008-09-12
the amount of connections is limited by the config files i think. oh and your total bandwidth obviously

---

