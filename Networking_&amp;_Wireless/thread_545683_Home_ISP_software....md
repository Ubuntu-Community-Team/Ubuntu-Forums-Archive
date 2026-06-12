---
title: "Home ISP software..."
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by RichJacot on 2007-09-07
Hello,

I guess let me start of by telling you what I would like to do and then what I have.

My daughter is off to college on a very tight budget. Her problem is netzero (free ISP) only allows 10hrs. a month of access. I'd like to be able to add a modem card to my Edgy system for her to dial into. Then have her be able to go back out my broadband FIOS connection. I don't even know if this is doable, but it sounds like it should be. Now on to what I have...

I have an Edgy install that is on 24/7 connected via 15/2mb FIOS connection. My phone service is Verizon Voicewing (VOIP). My daughter is within local calling area so she will not incur any LD charges.

Does anyone know what software is out there to accomplish this?

Any help is greatly appreciated!

---

### Post by Dark Hornet on 2007-09-07
Well....let me ask a few questions/comments....

1.  doesn't her college have its own network she can plug into?

2.  if not--you can hook a modem up to your server at home, and give her the number--the only issue I see with this is you are using VOIP, which puts all of your voice on a data connection (IP), and not your traditional phone line.

3.  Understand that if you decide to hook a modem up to your server, the fastest speed she will get will be the 56k modem speed, as this will become the bottle neck.

---

### Post by RichJacot on 2007-09-08
Hello,

She's not staying on campus, but when she is at school, yet she can.

I understang her max speed will be limited by her modem/mine, but the real question I have is how can I configure my system to allow her to dial into it (like an ISP), then let her surf, email, etc..

She'll dial my number, my system answer, she surfs and request to out my broadband come back in an upto her via the modem.

---

### Post by Phurious on 2007-09-08
You *MAY* be able to do something with SmoothWall - not an application for Ubuntu but a different distro itself [http://www.smoothwall.org]("http://www.smoothwall.org")

Don't think it is exactly what you want, but it is another option.

---

### Post by KCPokes on 2007-09-08
> **Phurious said:**
> You *MAY* be able to do something with SmoothWall - not an application for Ubuntu but a different distro itself [http://www.smoothwall.org]("http://www.smoothwall.org")

Don't think it is exactly what you want, but it is another option.

I agree.  Smoothwall has a PPP option that should allow someone to dial into the firewall.  You will probably find some related topics on their forums.

---

