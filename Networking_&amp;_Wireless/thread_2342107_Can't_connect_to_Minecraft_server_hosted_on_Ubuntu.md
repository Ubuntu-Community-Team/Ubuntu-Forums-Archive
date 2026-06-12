---
title: "Can't connect to Minecraft server hosted on Ubuntu Server 16.04"
date: 2016-11-03
forum: Networking &amp; Wireless
---

### Post by mw992 on 2016-11-03
First off, I know the Ubuntu Forums may not seem like the proper place to post a thread like this, but just bear with me for a moment. I believe my issue is more of a network type problem, rather than having to do with Minecraft specifically. I've tried getting help on other Minecraft server oriented forums, but haven't had any luck, and I feel like I might be able to get better help from people who are more knowledgeable about servers, firewalls, etc. 

So, just some background here... I have an OVH VPS that I've run a Minecraft server (Spigot) on for a few months. I haven't been able to connect to it recently (it times out) and I'm not sure why. I'm able to log in via SSH, other people can connect to it, and I'm able to connect to other servers. By default, it runs on port 25565, but if I change it to another port, then I am able to connect. Normally, this might suggest a firewall issue (I think), but I don't think that's the case since other people can connect, and I can connect to other servers. I've tried adding a firewall exception for port 25565 anyway and it still didn't work.

I thought that perhaps my router had something to do with it, so I connected directly to my modem via an Ethernet cable and it still wouldn't connect. I'm totally stumped and out of ideas at this point.
It just doesn't make sense that it used to work, other people can connect, I can connect to other servers, and that I am able to connect when it's running on a port other than 25565.

Any help would be greatly, greatly appreciated.

---

### Post by mw992 on 2016-11-06
Well I just give up...

---

### Post by igotananswer on 2016-12-05
I got a similar problem, and solved it by launching the server with openjdk-8 instead of openjdk-9.
I don't really understand the problem but it works that way.
I don't know if it's help but .. well.

---

### Post by mw992 on 2016-12-08
> **igotananswer said:**
> I got a similar problem, and solved it by launching the server with openjdk-8 instead of openjdk-9.
I don't really understand the problem but it works that way.
I don't know if it's help but .. well.

I was already using version 8, so I don't think that was my issue. I deducted that I was no longer able to connect to Minecraft servers that are hosted in Canada, which is weird... I'm guessing it has something to do with my DNS settings or ISP.

Thanks for replying at least. :P

---

