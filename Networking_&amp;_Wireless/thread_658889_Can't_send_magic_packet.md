---
title: "Can't send magic packet"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by MJ23 on 2008-01-05
I have my Ubuntu working as router(server) and i have several PC behind it. All of them are windows xp machines. What i want to do is to be able to wake up XP machines through the router. I'm connecting to router through the ssh and executing wake ona lan command. And it is not working. 
If I try to wake XP machine from another XP machine - i'm using SmartCode VNC manager with the builtin wake on lan feature it works for me.

Now this is how i've tried to wake it up.
First of all i've installed etherwake and wakeonlan tools.

wakeonlan -i 255.255.255.255 -p 7 00:04:61:9B:2A:7D
Ive tried to send it to broadcast, excact IP using differet ports - by the way from smartcode vnc it wakes up on different ports. 

etherwake -b 00:04:61:9B:2A:7D
same result. Nothing works.

MAC address is correct because it is saved in vnc manager where it works.

Appreciate any help.

---

### Post by roaldz on 2008-01-05
> **MJ23 said:**
> I have my Ubuntu working as router(server) and i have several PC behind it. All of them are windows xp machines. What i want to do is to be able to wake up XP machines through the router. I'm connecting to router through the ssh and executing wake ona lan command. And it is not working. 
If I try to wake XP machine from another XP machine - i'm using SmartCode VNC manager with the builtin wake on lan feature it works for me.

Now this is how i've tried to wake it up.
First of all i've installed etherwake and wakeonlan tools.

wakeonlan -i 255.255.255.255 -p 7 00:04:61:9B:2A:7D
Ive tried to send it to broadcast, excact IP using differet ports - by the way from smartcode vnc it wakes up on different ports. 

etherwake -b 00:04:61:9B:2A:7D
same result. Nothing works.

MAC address is correct because it is saved in vnc manager where it works.

Appreciate any help.
If the ubuntu box is a router, I´m assuming that it´s connected with 2 interfaces, this can cause some trouble..

---

### Post by MJ23 on 2008-01-05
Thanx for your answer! :)

I assume you know what the broadcast mean - so it wont cause any problem.

---

### Post by MJ23 on 2008-01-06
Anyone? 
Any ideas?

---

### Post by roaldz on 2008-01-06
> **MJ23 said:**
> Anyone? 
Any ideas?

Yeah, install a packet sniffer to listen on the interface you want it to work on, and then check if your wake on lan packet comes through. A good sniffer is wireshark:
**[Click here]("apt:wireshark")** to install wireshark.

ps. ik like that apt protocol handler:)

---

### Post by MJ23 on 2008-01-06
Ok, thanx for reply.

Yes, i have 2 interfaces. eth0 is an external and the eth1 is an internal. As my PC which i want to wake up is in my internal network the magic packet must be send by the eth1 interface. I have sniffed my network and found that the magic packets were sent by eth0 and it means that it was sent to the external network - my ISP network. And that is why my PC couldn't wake up.

So, the next question is: how can i configure wakeonlan to use a specific interface??

---

