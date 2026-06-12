---
title: "Eth0 not Connecting"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by bet77cing on 2008-11-26
Howdie,

I am very new to Ubuntu.. as you can see quite a greenie. I installed Ubuntu last week. And while in the process understanding Ubuntu and of getting my wireless to work on my HP dv6000... I lost the connection through my Ethernet card
 nVidia Corp MCP67 Ethernet (rev a2)

I am currently connected to the internet on another computer, through the same router. I restarted my computer, just to check the problem wasn't there.

I have it in DHCP. And I think the problem lies in the "local loopback" 127.0.0.1. I have read a couple threads, however I do not know what my static connection is... if that is really what I need to do to get the connection working. Perhaps I'm just not there yet and I need Ubuntu in plain language. haha :lolflag:

If you know of another thread that I should read, or know how to solve my problem... I would appreciate your input. Thank you

---

### Post by aeronotix on 2008-11-26
I had the same problem. I'm really trying to remember how I got it sorted. 

Go into your System>Network unlock it with your password. Then go on properties for that and check all them match what they're supposed to be, DHCP and stuff like that. Also, I don't think the loopback thing may be the problem 'cause mine is set the same.

Also can you, with your wired connection access your router or anything?

---

### Post by cariboo on 2008-11-26
Open a Applications-->Accessories-->Terminal and type:

```
sudo dhclient eth0
```

to see if you can connect to your router. 

One other thing to check, have you got mac address filtering set up in your router?

Jim

---

### Post by kieranchiru on 2008-11-27
Hi All,

I am installing ubuntu 6.06 server on dell pc, but it says No ethernet card detected, but firewall interface is persent. Can any tell me how to go ahead......


Thanks in advance

Kieran

---

### Post by rlzyoner on 2008-11-27
Also, may not apply to you, but for soem reason, my wired connection requires me to manually type in the dns server addresses.
This is most likely going to depend on your ISP configuration,i.e static ip address, dynamic ip address etc

---

