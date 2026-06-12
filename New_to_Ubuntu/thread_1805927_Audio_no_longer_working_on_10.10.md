---
title: "Audio no longer working on 10.10"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-07-16
When I first started using Ubuntu on my laptop I could get sound, but my headphone jack would never work. I looked through all the settings and searched for a while until I found where to switch the output from speakers to my headphone jack, and all was fine, for about two days. Now my mute light on my computer stays red, meaning off, and when it hit it the light remains red yet the volume meter on the screen switches between mute and unmute. The volume controls on both the screen and the computer itself will move the meter up and down, but no sound ever plays. I've muted and unmuted using both the sound options and the computer buttons, switched between both output options, nothing.

Anybody here experience this?

---

### Post by LowSky on 2011-07-16
What brand and model is the PC... we cant help if we don't have all the information.

---

### Post by jtarin on 2011-07-17
Type ["alsamixer"]("http://en.wikipedia.org/wiki/Alsamixer") in a terminal (without quotes) and ensure all ranges are unmuted and set as you would like.

---

### Post by Neoncamouflage on 2011-07-17
It's an HP Pavilion DV7-3173nr with 10.10 installed as the sole OS.

I don't know what happened, but I brought up the sound controls in the terminal, everything was alright. I fiddled around with it a bit, just seeing what all I could change, fixed it back the way it was, and now the sound works. To my knowledge it's still on the same settings as before, so it may be unrelated.

Thanks though guys. Go figure.

---

### Post by jtarin on 2011-07-17
When you closed it you updated the profile it was opened to.

---

