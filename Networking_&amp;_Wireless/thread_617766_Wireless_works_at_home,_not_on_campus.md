---
title: "Wireless works at home, not on campus"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by Joshgray on 2007-11-19
I just installed gutsy on my Thinkpad z61t laptop. I joined my WEP protected wireless network at home without a hitch, but I cannot join the WEP protected wireless network on campus. The SSID on campus is hidden, but I managed to set it so my network interface 'sees' it. That is, on the drop down menu of wireless networks the SSID shows up. When I try to join I get the dialogue to enter the passphrase, I do and then... nothing! After a while the dialogue comes back up. I know that I have entered the correct passphrase. Since the wireless works at home it seems that I wouldn't need to used ndiswrapper, am I wrong about this? I am a complete n00b, so none of this makes sense to me. I scanned the forums but all of the help seems to be for folks that can't get wireless to work at all, not my problem. Hopefully someone can give some help?

Thanks in advance,

Josh

---

### Post by shasan on 2007-11-19
Hmm... You don't happen to be at a school with a ram as its mascot, do you? Sounds like a similar problem to what I had. Which version of ubuntu are you running?

---

### Post by Joshgray on 2007-11-19
Indeed! Tarheels FTW... except when it comes to ubuntu wireless apparently. I am running gutsy gibbon (7.10). Have you figured it out? Thanks.

---

### Post by Whiffle on 2007-11-19
What wireless card are you using, and do you have more info about what that network requires?

---

### Post by Joshgray on 2007-11-19
My wireless card is made by Atheros, this is the device info in hardware manager: AR5212 802.11abg NIC

I don't know the exact specifications for the wireless network on campus, but when windows was previously installed on this laptop it connected no problem. So, there's definitely no hardware compatibility issues.

---

### Post by shasan on 2007-11-20
Yes, I'm on the school network right now. It's kind of tricky. I've found that going to the "Connect to other wireless network" and typing in the network name and WEP key can work sometimes. When I ran 7.04, I would have to enter the instructions from this help page: 

[https://help.unc.edu/restricted/4982](https://help.unc.edu/restricted/4982) (onyen required)

and then go to "connect to other wireless network...". Sometimes, it would then connect; sometimes, I'd have to run those commands listed in the help document again and it would work. Kind of finicky. Indeed. I have to say, though, that since updating to 7.10, I haven't had this problem.

Shoot me an email (shasan@email.unc.edu) if you still have problems; if nothing else I can get you in touch with some fellow Ubuntu users around campus who may be able to help.

---

