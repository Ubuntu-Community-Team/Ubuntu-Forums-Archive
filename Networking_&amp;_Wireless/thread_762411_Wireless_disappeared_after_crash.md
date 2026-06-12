---
title: "Wireless disappeared after crash"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by amosharper on 2008-04-22
Hi,

I have an Acer Aspire 5051 laptop with Ubuntu 7.10 installed (alone). I left the laptop on, plugged into the mains, for about 20 minutes. When I came back, the power light was still on but the screen was off. When I shook the mouse, nothing happened, and when I pressed a key, nothing happened. I tapped the power button (which is only bound to bring up the 'shut down' dialog) and nothing happened that I could see. I pressed and held the power button, and it turned off.

When I turned it back on, it no longer allowed me to use my wireless - hovering over the Network icon in the top-right gave the tool Tip 'No Network Connection', and the network manager only showed the possibility of wired connection.

Can I get my connection back? If so, how? If I need to provide more detail, please tell me to.

Thanks greatly in advance. 

- Amos

---

### Post by blastus on 2008-04-22
I have found with my wireless laptop that sometimes the connection just drops. Sometimes I can get it back other times I can't without rebooting. I encountered one situation where even rebooting did not bring back wireless. I had to turn off my laptop and then turn it back on again.

What my ISP recommends (and this may be applicable to wireless also) is to turn off and unplug all your computers, modem(s), and router(s) (if applicable.) Then turn them back on again.

---

### Post by Crafty Kisses on 2008-04-23
> **blastus said:**
> I have found with my wireless laptop that sometimes the connection just drops. Sometimes I can get it back other times I can't without rebooting. I encountered one situation where even rebooting did not bring back wireless. I had to turn off my laptop and then turn it back on again.

What my ISP recommends (and this may be applicable to wireless also) is to turn off and unplug all your computers, modem(s), and router(s) (if applicable.) Then turn them back on again.

I had the same issue, and still have it until this day. The weird thing is when I switched my Wireless off on my laptop, it worked, and when I switched the Wireless switch on, it didn't work.

So I went into Terminal while it was on and typed: ```
netstat
```
It appeared it was getting a connection, but wouldn't work, very strange issue and until this day it still boggles me.

---

### Post by amosharper on 2008-04-23
Thanks for your replies.

Wireless doesn't work if my wireless light is on or off. 

NetStat tells me I'm connected.

All other wireless computers in my house (all of them) work. I have no other Ubuntu machines.

Shutting it down and rebooting didn't work.

Any other ideas?

Thanks.

---

