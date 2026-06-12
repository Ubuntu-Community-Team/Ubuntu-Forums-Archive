---
title: "Wireless Works Fine, Then Just Stops Next Day?"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by kyle5077 on 2006-09-01
Ok, so after going trough hell to get my Broadcom working, i finally get it using the bcmxx w/ fwcutter and adding ndiswrapper to the blacklist. It was working fin, then I levae the computer on overnight, come back this morning, and nothing. No signel. I tryed rebooting, reconnection, reconfiguring, etc...

Is this a known issue with bcmxx? I cant find any info on it just stopping after it was succesfully working.

TIA

---

### Post by kyle5077 on 2006-09-01
Ok, tell me if this makes any sence...the LAN port needs to be active for the wireless to connect. Weather it be a crossover cable to another computer, or an actual internet connection, as long as something is plugged into the LAN on boot, the wireless card works fine, and after it acquires an address i can unplug the LAN...wtf?

---

### Post by yellerKat on 2006-09-01
That's exactly what I get; when the wifi gives up interest, a wired LAN connection wakes it up again. Interesting, but not critical, for me.

---

### Post by DanielNuyu on 2006-09-02
I've also experienced this unusual link between eth0 and eth1. It doesn't make any sense, but is there, clearly.

---

### Post by c-prompt on 2006-09-02
Is it a Dell?  I always noticed that when you use your wireless, the actiivty lights on the lanport flash accordingly.

Also, if it is a Dell, a friend of mine has his broadcom wireless working fine without this eth0-eth1 problem.

---

### Post by kyle5077 on 2006-09-02
> **c-prompt said:**
> Is it a Dell?  I always noticed that when you use your wireless, the actiivty lights on the lanport flash accordingly.

Also, if it is a Dell, a friend of mine has his broadcom wireless working fine without this eth0-eth1 problem.

Nah, its a Vaio laptop with a Belkin PCMCIA card that uses the Broadcom 43xx chipset. 

Atleast im not the only one having this odd problem...lol

---

### Post by kyle5077 on 2006-09-08
Anyone else have any ideas?

---

### Post by dannyboy79 on 2006-09-08
i read somewhere that you need to comment out the interface that you DON'T want to use in your /etc/interfaces file. So if your eth0 is the interface that you want to use than comment out the eth1 interface. I read that basically your computer is having a tough time deciding which interface to use so it never gets an ip. Well, your comment, "as long as something is plugged into the LAN on boot, the wireless card works fine, and after it acquires an address i can unplug the LAN...wtf?" makes perefectly good sense, your computer is using your lan connection to get it's ip, once it has it and you unhook the lan line, it somehow switches interfaces and uses the other interface. I am a newbie so I unfortunately can't help you anymore than I already have, if I have evn helped you at all. Sorry if I didn't.

---

