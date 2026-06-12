---
title: "Rt2500 Wicd problems"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Nerfperson on 2007-10-01
Alright, been trying to get wireless on a laptop with PCMCIA card with rt2500 chipset for too long now.

Tried just about every guide I could find; as of now I am using Wicd for managing.

I can see my network, wpa is set up, but it just won't connect.

Don't know what to do anymore. Every few seconds or so the activity light will flash, and it will say I'm connected for half a second but thats it.

---

### Post by wieman01 on 2007-10-02
> **Nerfperson said:**
> Alright, been trying to get wireless on a laptop with PCMCIA card with rt2500 chipset for too long now.

Tried just about every guide I could find; as of now I am using Wicd for managing.

I can see my network, wpa is set up, but it just won't connect.

Don't know what to do anymore. Every few seconds or so the activity light will flash, and it will say I'm connected for half a second but thats it.
WICD does not fully support RT2500 yet. Have you given "ndiswrapper" a thought? It enables you to use tool such as WICD and Network Manager.

---

### Post by Nerfperson on 2007-10-02
Already used ndiswrapper with a Winxp driver. No good.

---

### Post by kevdog on 2007-10-02
What driver are you using now -- the one shipped with ubuntu or the serial monkey rt2500 driver??

You can find out with
lshw -C network

---

### Post by wieman01 on 2007-10-02
> **kevdog said:**
> What driver are you using now -- the one shipped with ubuntu or the serial monkey rt2500 driver??

You can find out with
lshw -C network
Ubuntu ships with Serialmonkey's driver in fact...

---

### Post by kevdog on 2007-10-02
Hmm, I didnt know that -- are the serial monkey driver's that ship with Feisty -- these must be the older versions?? Correct?? 

Thanks for the update -- never knew that since when you check both the old and newer drivers with the modinfo rt2500, only the newer drivers I downloaded and compiled from the serial monkey site actually state serial monkey in the info, the older ones do not!

---

### Post by wieman01 on 2007-10-02
> **kevdog said:**
> Hmm, I didnt know that -- are the serial monkey driver's that ship with Feisty -- these must be the older versions?? Correct?? 

Thanks for the update -- never knew that since when you check both the old and newer drivers with the modinfo rt2500, only the newer drivers I downloaded and compiled from the serial monkey site actually state serial monkey in the info, the older ones do not!
Aren't they the only ones that develop an open-source driver for Ralink? I thought so. But perhaps I am mistaken there. 

I'll check. If you know something, appreciate if you posted.

---

### Post by unisol on 2007-10-02
what wireless window  driver did you use with ndiswrapper? the xp driver? give the win 98 driver a try.

---

### Post by kevdog on 2007-10-02
I dont know any "secret information".  It was definitely a question.  Ill look around and see what I can find.  I know serial monkey develops an ra driver, however Im not sure if they are the only one who develops an open source ra driver.

---

### Post by Nerfperson on 2007-10-02
> **unisol said:**
> what wireless window  driver did you use with ndiswrapper? the xp driver? give the win 98 driver a try.

Upon further inspection, the Rt2500.inf file is the same for all versions of windows; it is the other files like rt2500.sys that appear to be distinct.

Not really sure what this means. Those won't install with ndiswrapper (didn't think they would).

---

### Post by kevdog on 2007-10-02
How about compilation of the rt2500 cvs drivers from serial monkey??

---

