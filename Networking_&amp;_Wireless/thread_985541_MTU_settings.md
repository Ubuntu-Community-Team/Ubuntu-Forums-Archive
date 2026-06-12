---
title: "MTU settings"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by alexplay3 on 2008-11-17
So i'm using Debian Lenny Testing but i think it also applies to Ubuntu since the method is the same.

I changed my MTU settings adding the following line in /etc/network/interfaces:

post-up ifconfig eth0 mtu 1500

And it works perfectly everytime i boot up, the only annoying problem is that the Connection/Network icon says "No Network Connection" although i'm still connected to the internet and can navigate without problems.

But if i just do:

# ifconfig eth0 mtu 1500

It also changes without problems while still saying i have network connection.

So the question is: how to make so the icon says i'm connected to the internet while still keeping the post-up command? or if there's another method please let me know.

Thanks in advance.

---

