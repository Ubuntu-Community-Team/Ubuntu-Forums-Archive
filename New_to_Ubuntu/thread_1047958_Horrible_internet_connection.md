---
title: "Horrible internet connection"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by shaolinmilk on 2009-01-22
When I play online games, I keep on getting disconnected. Ever since I tried to set up my static ip, I keep on getting disconnected. I set it back to normal and the problem still occurs. I play a game and all of a sudden, I get disconnected. The problem is persistent and has been going on for a while now. Does anyone know how to fix this and help me keep a stable connection? I don't think it's my game because my MSN(emesene) signs out as well.

---

### Post by jerome1232 on 2009-01-22
Are you connected wireless or wired?

---

### Post by shaolinmilk on 2009-01-22
I'm wired up. 

ps. I have two ethernet card. One that came with my motherboard and one I bought recently. The one with my motherboard is broken so I bought a new one. Maybe they're conflicting with one another?

---

### Post by jerome1232 on 2009-01-22
Generate some network traffic (download a file or something) and then type ifconfig into a terminal, are there large amounts of errors?

I think the first thing I would suspect is a bad ethernet cable or a bad nic. *Possibly* a bad driver for you nic. I guess knowing what kind of ethernet card might help if someone knows that the driver for your card is terrible or something like that.

Do have another ethernet cable you can test with?

---

### Post by shaolinmilk on 2009-01-22
There's no error when I tried that. I just disabled my onboard LAN and hopefully that fixes me problem. I tested my internet with another cable and it's the same. The card I have is a D-Link DFE-538TX.

---

