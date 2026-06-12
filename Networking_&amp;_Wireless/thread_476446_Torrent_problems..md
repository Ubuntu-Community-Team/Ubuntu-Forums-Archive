---
title: "Torrent problems."
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Louie on 2007-06-17
Hello Ubuntu Users, hope this forum may work for my question, else please move it. 

I got a very disturbing problem with all my torrent programs, I never got any speed when I downloading from anyone using torrents. I've tried ktorrent, azureus and rtorrent but I got the same problem in every program. Sometimes I can get good speed in 1-2 minutes and then Im down at 1-2 kb/s again. I am used to torrents so I know what seeders/lechers is and I got a port open in my firewall. I've tried In different networks but the problem remains. Very slooow/no speed at all. Is there any software firewall in Ubuntu Feisty that blocks this kind of connections? Because the worst thing is that the downloading works perfectly in windows... I don't want to use that system just becuse my stupid torrents don't work as it should. 

Is there anyone with the same problem or do you have any idéas?
Please help me out.

Best wishes :)

---

### Post by Biggus on 2007-06-17
You may have to open the port in, what I understand to be the inbuilt, firewall, called iptables I think.

I don't know terribly much about it, but I can get by by using the 'Firestarter' program, which I understand to be a GUI for basic manipulation of the iptables program.

I access it by System->Administration->Firestarter

---

### Post by Louie on 2007-06-17
> **Biggus said:**
> You may have to open the port in, what I understand to be the inbuilt, firewall, called iptables I think.

I don't know terribly much about it, but I can get by by using the 'Firestarter' program, which I understand to be a GUI for basic manipulation of the iptables program.

I access it by System->Administration->Firestarter

Firestarter isn't installed on my computer but iptables is, shall i install firestarter?

---

### Post by Louie on 2007-06-17
Do you think it help if i remove iptables?

---

### Post by Biggus on 2007-06-19
I don't think you can remove iptables, tbh.

I thought that every ubuntu edition had firestarter with it by default, my apologies.

You may be able to install it through the 'Add/Remove' option in your applications menu, or, failing that, the 'Synaptic Package Manager' will probably have it in there somewhere.

---

### Post by zero-9376 on 2007-06-19
Im pretty sure iptables is an important part of the system and should not be removed. Also I dont think that the firewall capabilities of iptables are enabled on a normal ubuntu install as there aren't any services running by default that need the protection. I therefore doubt that this is the problem, I had similar issues when I started using various torrent programs and Azureus was the only one that would work properly for me. I can only say that Im not having your issue now, and the only change I have made which may affect this issue is to disable ipv6 on my system. There are instructions for this either on the forum or just google, its pretty easy and makes general browsing faster for me too.

---

