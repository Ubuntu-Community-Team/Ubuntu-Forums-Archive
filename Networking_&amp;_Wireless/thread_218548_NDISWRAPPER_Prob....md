---
title: "NDISWRAPPER Prob..."
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by MiniZiper on 2006-07-18
Ok, I have ndiswrapper isntalled (thanks to automatix)
I open the gui version (sudo ndisgtk) it opens up fine, then i sellect the driver (AutoRun.inf), but nothing happens:(  and i get this on konsole:
[COLOR="DarkOrange"]FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument[/COLOR]

So yea.... whats the problem?? thats alchemy to me still](*,) , evne thoguh I have a little experience with Linux.:mrgreen: 

Thanks!!:D 

P.S. the emoticons in this forum are awesome :mrgreen:

---

### Post by notoriousdbp on 2006-07-18
are you using kubuntu?

---

### Post by MiniZiper on 2006-07-18
Yes

---

### Post by DJ Scribblinni on 2006-07-18
Are you using the AutoRun.inf as the file you use for the driver for your wireless card?  Last time I checked Windows used that to determine what happens when a CD is put in the drive, not as the driver to control the card...  If I'm wrong, so be it, if not, you need to find the .inf that is used for your card.

---

### Post by MiniZiper on 2006-07-18
Ur right, but I still get the same error.... if I try the otehr .inf files....

---

### Post by DJ Scribblinni on 2006-07-18
What type of network card are you trying to use?

---

### Post by MiniZiper on 2006-07-18
Im trying to use a Linksys card, the one u insert on the card thing on the side of the laptop.the model is uh... WPCG5 or something like that... I don't think the model would matter if ndiswrapper doesnt work...

---

### Post by DJ Scribblinni on 2006-07-18
If I'm thinking correctly, that error comes out when the wrong driver is being used for the card you have.  If not, I can't help ya out.  Here's a quick link to possibly help you, if perhaps that error is just a wrong driver being tried.  
[http://www.ubuntuforums.org/showthread.php?t=5645]("http://www.ubuntuforums.org/showthread.php?t=5645")

---

