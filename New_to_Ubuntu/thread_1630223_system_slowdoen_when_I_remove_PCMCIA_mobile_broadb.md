---
title: "system slowdoen when I remove PCMCIA mobile broadband card."
date: 2010-11-24
forum: New to Ubuntu
---

### Post by waynefoutz on 2010-11-24
I'm not exactly a beginner, but this has me stumped. I'm at home right now where I have a cable modem and wifi. Normally, this laptop, a Dell Latitude D531 travels with me, and I've pretty much used a Sprint PCMCIA aircard, a Pantech PX-500, as my primary internet access. 

 I installed Ubuntu 10.04 last time I was here, bout a month ago. I got home today, removed the card and connected to my wifi network. When I run anything intensive, such as a 3d game, I'm getting pauses, where the whole system just slows to a crawl, then beack to speed for a few seconds, then back to a crawl again. I got to tinkering, and the only thing I could think of that's different now than this morning is that I removed the mobile broadband card. So I slid it into the slot and started up  a game of Nexuiz. It ran smooth as silk. I then closed the game, removed the card, and the problem returned. 

The only thing I can imagine is there might be some process running looking to use that particular card. Anyone have a clue what that could be?

---

### Post by wojox on 2010-11-25
Sounds like a Driver issue. Have you checked that out?

---

### Post by QLee on 2010-11-25
[QUOTE=waynefoutz]...
The only thing I can imagine is there might be some process running looking to use that particular card. Anyone have a clue what that could be?[/QUOTE]

I'm going to make a guess, ...and guesses are frequently about as useful as assumptions but ...

Is the network manager connection for the aircard optioned to "auto"? Perhaps, it's trying it for broadband WiFi whenever it's installed, even though you have a different connection already working. Not sure if that is a clue or not, some people think I'm clueless most of the time.

---

### Post by waynefoutz on 2011-01-29
I finally solved this problem last night after a reinstall of 10.04. Everything ran fine until I ran the updates, then the problem returned. My system would freeze momentarily in what seemed like 30 seconds intervals, but magically the problem would disappear when you slid a PCMCIA card into the laptop's slot. So I rebooted into the original kernel, and lo and behold, the system was responsive again. So I locked the older kernel in synaptic package manager, and removed the newer updated kernel. Problem solved. I still have no idea what the PCMCIA card had anything to do with it. Truly bizarre.

---

