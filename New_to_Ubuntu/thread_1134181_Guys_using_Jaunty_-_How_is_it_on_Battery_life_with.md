---
title: "Guys using Jaunty - How is it on Battery life with notebooks?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-23
Just curious. I'm on 8.04 now, and with the latest kernel, it's showing an estimated 2.5 hours.

How's Jaunty on battery life?

---

### Post by ddrichardson on 2009-04-23
Been using 9.04 UNR for a month and its about the same, I haven't noticed any big difference.

---

### Post by sdennie on 2009-04-23
Ubuntu has most (if not all) of the power savings features disabled by default.  I believe this is done because, as a generic release, they want to support everyone and some of the options cause problems for people.  If you are interested in power savings, I recommend looking at [www.lesswatts.org](www.lesswatts.org) and [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  The latter being an example on how the advice from the former can be applied.

---

### Post by ddrichardson on 2009-04-23
That's true Ubuntu's PM is fairly vanilla but in the case of Ubuntu Netbook Remix, power management is a design element - mentioned in the [9.04 release announcement]("http://www.ubuntu.com/news/ubuntu-9.04-unr"). I'm just saying that even so and having ensured the steps recommended above I don't see a significant improvement between releases on the Acer Aspire One but your mileage may vary.

---

### Post by sdennie on 2009-04-23
> **ddrichardson said:**
> That's true Ubuntu's PM is fairly vanilla but in the case of Ubuntu Netbook Remix, power management is a design element - mentioned in the [9.04 release announcement]("http://www.ubuntu.com/news/ubuntu-9.04-unr").

I don't doubt that one bit.  But, power savings on linux is like an art.  With Windows it isn't because the vendor likely tuned the OS to be good on power savings.  Really crazy things like having a kernel with ASPM enabled and disabling the USB subsystem can make a *huge* difference.  Any generic release of Ubuntu can't tune the power savings for your specific machine so, unfortunately, if you care about power savings, the burden is on the user.

---

### Post by ddrichardson on 2009-04-23
I understand that but you missed where I said I've also followed steps at lesswatts.org.

Huge difference is relative - the problem with systems I'm running UNR on, such as the Aspire One is that the battery has quite a low AH rating, so realistically you're never going to achieve much more than 2.5 hours. That and the fact that there use often relies on wireless which is a real drain.

The other problem of course is that people often make the switch to Ubuntu after having had a laptop running Windows for some time. BIOS implementation and driver tweaking aside, batteries degrade over time and the increases in longevity that can be achieved by tweaking ultimately tends to be overcome by degradation.

---

### Post by steve101101 on 2009-04-23
+1 laptop battteries just dont last. People def. compare battery life when it was new with windows compared to when its a few years old with ubuntu.

---

### Post by sdennie on 2009-04-23
> **ddrichardson said:**
> I understand that but you missed where I said I've also followed steps at lesswatts.org.


I didn't see that actually.

> 
Huge difference is relative - the problem with systems I'm running UNR on, such as the Aspire One is that the battery has quite a low AH rating, so realistically you're never going to achieve much more than 2.5 hours. That and the fact that there use often relies on wireless which is a real drain.


I don't own one so don't know.  Your analysis sounds like it comes from experience and knowledge so I don't doubt you.

> 
The other problem of course is that people often make the switch to Ubuntu after having had a laptop running Windows for some time. BIOS implementation and driver tweaking aside, batteries degrade over time and the increases in longevity that can be achieved by tweaking ultimately tends to be overcome by degradation.

Yes, that is certainly a big problem.  And one that users may find hard to understand.

---

### Post by ddrichardson on 2009-04-23
> **sdennie said:**
> I didn't see that actually.
I re-read it and I probably didn't make it clear.

---

### Post by crjackson on 2009-04-23
I have 4 laptops with generic installs of windows (from user owned CD/DVD - not vendor installed/tuned). Each of them also has Ubuntu installed (3 with 8.04.2 - 1 with 9.04).

I see NO difference in battery life from one OS to the other.

---

### Post by sdennie on 2009-04-23
> **crjackson said:**
> I have 4 laptops with generic installs of windows (from user owned CD/DVD - not vendor installed/tuned). Each of them also has Ubuntu installed (3 with 8.04.2 - 1 with 9.04).

I see NO difference in battery life from one OS to the other.

That's because a generic install doesn't tune the machine properly and so they are probably running with similar default settings.  I have no idea how to tune power savings on Windows but, the links I've posted above might contain some ideas about how to do it on Ubuntu if it's a concern.

---

### Post by crjackson on 2009-04-23
> **sdennie said:**
> That's because a generic install doesn't tune the machine properly and so they are probably running with similar default settings.  I have no idea how to tune power savings on Windows but, the links I've posted above might contain some ideas about how to do it on Ubuntu if it's a concern.

That was the point I was making. They are similar unless tweaked. It's not a concern for me. I was illustrating that Win isn't particularly better or worse.

---

