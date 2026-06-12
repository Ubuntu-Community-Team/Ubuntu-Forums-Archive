---
title: "Spotty/ SLOOW wireless internet connection"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by -emory- on 2007-10-01
Hey everyone, this issue sort of just came out of no where. For about 2 months now I've been running Ubuntu dual booted with a woindows xp partition. I worked for some time getting wireless to work but was finally sucecssful, and it ran swimmingly. Last week I dropped the windows partition completely and made my computer solely ubuntu. I'm loving it. Compiz is just too beautiful. Unfortunately, since then it seems my connection has been spotty. I've got my laptop running xubuntu in my lap as I type this and it's recieving the home network signal at around 85-90 percent. Meanwhile my desktop (which used to get about 90 percent) is staying right around 30 percent, when it has anything at all. The connection is slow and spotty atbest, and non existent much of the time.Specs: I'm running 7.04 Feisty with compiz on an HPa510n with 512 megs ram. The wireless card is a D-Link 620 with ndiswrapper (nd possibly rtl-wifi. After wokring on wireless for a few days, it magically started working) My router has dd-wrt and is 3 floors below me at the office. I configured the router so that supposedly it is giving my desktop the majority of the bandwidth for my network, but it still isn't helping, making me think that the problem probably lies with drivers, or with my ubuntu setup. Thanks for any and all help
Emory

---

### Post by noob12 on 2007-10-02
> Meanwhile my desktop (which used to get about 90 percent) is staying right around 30 percent, when it has anything at all

Not sure if this will be of any help, but assuming you didn't change any of the drivers between those two times, it sounds like you may have an RF reception or interference issue.  Check your antenna.  If your AP is below you, keep the antenna horizontal.   Movement of furniture/appliances on the intervening floors may have had an impact too.

---

### Post by -emory- on 2007-10-03
well I imagine I changed drivers, at least when I switched to Ubuntu. After I broke, and then refixed my wireless card yesterday, I realized that to get it to work I had to use rtl-wifi drivers. I don't havea phone up hear, and nothing has changed as far as placement. Are the drivers still ruled out? 
thanks
emory

---

### Post by -emory- on 2007-10-03
oh also my laptop recieves 89 percent right now, and i'm sitting at my desktop computer desk with the laptop in my lap (and wow that was a lot of almost oxymorons....)

---

### Post by noob12 on 2007-10-04
The drivers can have an impact.  When I read this:

> I worked for some time getting wireless to work but was finally sucecssful, and it ran swimmingly. Last week I dropped the windows partition completely and made my computer solely ubuntu. I'm loving it. Compiz is just too beautiful. Unfortunately, since then it seems my connection has been spotty.

I thought this meant you had just dropped the Windows partition not reinstalled everything.   I'd say anything you changed between things going "swimmingly" and things being "spotty" is suspect.

---

### Post by -emory- on 2007-10-04
Well, since the ubuntu installation was not the first partition I couldn't just drop windows, what I did was backup everything to an external hard drive, then just reinstall ubuntu completely over the entire hard drive and then reload everything from the backup I made.

---

