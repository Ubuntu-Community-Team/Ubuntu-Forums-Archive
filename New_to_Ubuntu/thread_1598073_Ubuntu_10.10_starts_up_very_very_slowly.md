---
title: "Ubuntu 10.10 starts up very very slowly"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by richdytch on 2010-10-16
Hi there, 

I decided a short while ago to start using Ubuntu on my desktop at home: 

AMD Athlon 64 3700 - 2.2GHz
2GB RAM

I've used Ubuntu 9.x before when I had a very very basic Dell desktop, much lower spec than this, and it ran wonderfully fast. But now I've installed 10.10 on the AMD machine, it takes about 10 minutes minimum to boot up and to get logged in - to a point where I can open a browser or suchlike. 

When I first installed the OS and rebooted, the system hung, displaying a message saying "IRQ 16: Nobody cared" and recommending that I use irqpoll. The second time I booted up, it displayed a different message, saying that it was disabling IRQ 19.

I looked into irqpoll and it seemed that a number of people were experiencing similar problems, and that irqpoll had sorted them out. I added it to the grub boot list (I think that's what it's called  - anyway, I put it within quotes after "quiet spash" within the relevant line, as directed) and it has made no difference. 

I should point out that the system once up and running is *just* about usable but very slow. I've taken to going off and making a cup of tea while I wait for Firefox to start up (haven't sorted out preload yet) and menus are quite slow to appear, loading their icons up a few seconds later. Definitely nowhere near the user experience I had when I ran Ubuntu on the old Dell. 

Yet, CPU performance seems to idle between 7 and 12%, although I've not tried anything particularly demanding yet. Spare RAM is plentiful. Something in there is obviously not happy and grinding quite badly. 

Any advice would be very welcome - particularly in the diagnostic area - I'm pretty much a newbie to Linux in general, although I hope to learn a lot more. 

Thanks, 

Rich.

---

### Post by peter27 on 2010-10-26
> **richdytch said:**
> The second time I booted up, it displayed a different message, saying that it was disabling IRQ 19.


I have the same problem with 10.10.

---

