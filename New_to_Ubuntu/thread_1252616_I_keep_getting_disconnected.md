---
title: "I keep getting disconnected"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by malaikaangel on 2009-08-29
Hello,

I seem to have a problem with network manager, I get disconnected suddenly after some time. Oddly there are days when everything works fine and others like today when I get disconnected every five minutes. I have to re-activate my network connection (un plug and re plug ethernet cable or right click on the network manager icon) every time.

Is there a way to check if it is a problem with Ubuntu/my laptop/ my access provider?

Thanks

---

### Post by mapes12 on 2009-08-29
Sounds like router problem. Does rebooting the router do any good?

---

### Post by malaikaangel on 2009-08-29
> **Re: I keep getting disconnected** 			
 			 			 		   		 		 		Sounds like router problem. Does rebooting the router do any good?


no, I still get disconnected :(

---

### Post by MrWES on 2009-08-29
> **malaikaangel said:**
> Hello,

I seem to have a problem with network manager, I get disconnected suddenly after some time. Oddly there are days when everything works fine and others like today when I get disconnected every five minutes. I have to re-activate my network connection (un plug and re plug ethernet cable or right click on the network manager icon) every time.

Is there a way to check if it is a problem with Ubuntu/my laptop/ my access provider?

Thanks

I've recently run into the same issues. Which network card are you using?
```
lspci
```

Disregard, I just re-read your original post, you're not on a wireless connection

---

### Post by warreno on 2009-08-29
My ISP has periodic disconnect problems too. I use a high-speed cable modem with a fixed IP, but from time to time I lose internet (and telephony) service.

It took a long time to track down what the problem was. Seems the apartment I live in has never had an upgrade in its internal cabling, and after 25+ years those cables have degraded to the point that I'm subject to intermittent connection failures. The only definite fix will be to replace all the internal cabling.

Sometimes restarting the modem helps; other times I'm out of luck until the signal strength is sufficient to get me online again. There doesn't seem to be any correlation with temperature, weather, or number of chickens sacrificed under a full moon. It's entirely unpredictable.

Also, down the pipe a bit, I use an old AirPort base station (pre-Extreme) to connect. I've opened some custom ports to let Vuze run. After an unpredictable amount of time, the AirPort just chokes and stops sending or receiving, and I have to reset it. I mention it here because it may or may not be relevant to your situation, in one way or another. TTBOMK the only way to fix that will be to replace the old AP with an Extreme base station, since the old model hasn't been supported by Apple since 2005.

Is it possible you're experiencing something similar to my problems with old cabling? If so, a call to your provider is probably the best way to start.

---

### Post by malaikaangel on 2009-08-29
> Is it possible you're experiencing something similar to my problems with old cabling?

I don't think so, it's a new house and the internet cabling was done only a couple of months ago.

The other thing is that I live in Kinshasa (in the Congo) and very few computer technicians have heard of ubuntu so as soon as there's a problem, they tell me to switch back to windows. That's why I'd like to check first if it is a problem with the hardware/ubuntu/internet provider.

---

### Post by warreno on 2009-08-29
> **malaikaangel said:**
> The other thing is that I live in Kinshasa (in the Congo) and very few computer technicians have heard of ubuntu

That is the definition of irony.

To me it smells like a hardware (network) issue of some sort, including but not limited to problems with your ISP.

Is it possible for you to get another ethernet card, plug it in and see if that behaves more consistently?

Also, how old is the PC, and is it sitting in an environment that subjects it to wide temperature or humidity variations? It's possible that all you might need to do is open the PC's case, remove and re-seat the card.

Afterthought: Have you considered replacing the cable? It might have a dodgy wire in it.

---

### Post by t0p on 2009-08-29
> **malaikaangel said:**
> 
The other thing is that I live in Kinshasa (in the Congo) and very few computer technicians have heard of ubuntu

> **warreno said:**
> That is the definition of irony.


Why's that ironic?

---

### Post by warreno on 2009-08-29
> **t0p said:**
> Why's that ironic?

Oh, [no reason]("http://www.ubuntu.com/products/WhatIsUbuntu"). (Scroll to the bottom.)

---

### Post by malaikaangel on 2009-08-29
The computer is fairly new, I got it in December and it's on my desk. It could be the temperature as it can get very hot around here.

> Is it possible for you to get another ethernet card, plug it in and see if that behaves more consistently?


Afterthought: Have you considered replacing the cable? It might have a dodgy wire in it.

I'll get someone to do it for me as I'm a total noob. I'll post the results of the operation.

---

### Post by warreno on 2009-08-29
> **malaikaangel said:**
> The computer is fairly new, I got it in December and it's on my desk. It could be the temperature as it can get very hot around here.

I'll get someone to do it for me as I'm a total noob. I'll post the results of the operation.

Back when I edited analog video, twentymumbledysometing years ago, the DVE (Digital Video Effects) box periodically just stopped working. The fix was always to re-seat the add-in cards. To do that I'd power it down, lift out each individual card from its socket, and plug it right back in again. The contacts were copper, and over time, and with heat expansion, they lost some of their conductivity. Re-seating them always fixed it.

I've seen precisely the same situation in modern machines, such as Dell PCs and home-built systems. Worth a try. You don't have to worry about messing anything up; just shut off the PC, open the case, unscrew the card anchor and lift and replace the card.

That's assuming the ethernet jack isn't soldered right into the motherboard, which it might be. In that case, I'd be highly suspicious of the cable. Especially if it seems it's got worse lately — the more those cables get unplugged and reconnected, the more likely it is that a loose connection will just get more loose.

---

### Post by t0p on 2009-08-29
> **malaikaangel said:**
> 
The other thing is that I live in Kinshasa (in the Congo) and very few computer technicians have heard of ubuntu

> **warreno said:**
> That is the definition of irony.

> **t0p said:**
> Why's that ironic?

> **warreno said:**
> Oh, [no reason]("http://www.ubuntu.com/products/WhatIsUbuntu"). (Scroll to the bottom.)

From [www.ubuntu.com/products/WhatIsUbuntu]("http://www.ubuntu.com/products/WhatIsUbuntu"):

> What does Ubuntu mean?

Ubuntu is an African word meaning 'Humanity to others', or 'I am what I am because of who we all are'. The Ubuntu distribution brings the spirit of Ubuntu to the software world.You think it's ironic that a Congolese tech knows nothing about an OS which is named with "an African word"?

Would you also think it's ironic if a Spanish tech knew nothing about an OS with,say, a Czech name? Or a Norwegian name?

(Hint: Congo is a country; Africa is a *continent*.)

---

### Post by malaikaangel on 2009-08-29
> You don't have to worry about messing anything up; just shut off the PC, open the case, unscrew the card anchor and lift and replace the card.

Thanks. I'll try that.

---

### Post by warreno on 2009-08-29
> **t0p said:**
> From [www.ubuntu.com/products/WhatIsUbuntu]("http://www.ubuntu.com/products/WhatIsUbuntu"):

You think it's ironic that a Congolese tech knows nothing about an OS which is named with "an African word"?

Would you also think it's ironic if a Spanish tech knew nothing about an OS with,say, a Czech name? Or a Norwegian name?

(Hint: Congo is a country; Africa is a *continent*.)

Good point. On the other hand, I would find it odd if someone from England, for instance, didn't know about *European* customs that took place in France, or was nonplussed by a term such as *je ne sais quoi*.

A continent is a large place, but global communications among nations make continents less vast all the time.

So yes, the idea of one person in Africa not knowing a word used by another person in Africa is a bit ironic, much as might be so for someone from Washington state to be baffled by Louisiana Cajun dialect.

And FWIW, the "Meaning" reference on the Ubuntu page omits to mention which nation actually uses the word. It could as easily be Congolese as anything else, based on that limited information.

---

### Post by warreno on 2009-08-29
> **malaikaangel said:**
> Thanks. I'll try that.

Hope it works. You might also feel tempted to vacuum out the machine a little, if you get the kind of dust we find in Arizona. Just be gentle, if you do.

---

### Post by malaikaangel on 2009-08-29
"Ubuntu" is used in Kinyarwanda and Kirundi (spoken in Rwanda and Burundi, countries neighbouring Congo). The word can be understood by anyone who speaks a bantu language (the origin of quite a few sub-saharan languages)...

---

### Post by malaikaangel on 2009-08-29
So I lifted and replaced the card, nothing happened. Then I tried to re set my connection so I deleted the "wired connection" and set it up again (re entered my IP address etc.) and it's working. I haven't been disconnected since. We'll see how long this lasts.

---

### Post by warreno on 2009-08-30
> **malaikaangel said:**
> So I lifted and replaced the card, nothing happened. Then I tried to re set my connection so I deleted the "wired connection" and set it up again (re entered my IP address etc.) and it's working. I haven't been disconnected since. We'll see how long this lasts.

Oh! How interesting.

---

