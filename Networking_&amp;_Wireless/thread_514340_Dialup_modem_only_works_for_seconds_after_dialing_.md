---
title: "Dialup modem only works for seconds after dialing in"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by Shilahr on 2007-07-31
Hello y'all!

First, I gotta say I really love Ubuntu and this community - even though I'm still a Linux n00b, I had little trouble setting up most things, and anytime I had a problem up to now, all it took was some searching here and in the wiki and I was good to go again!

This time, however, I'm kinda stumped...

I am trying to enable Internet access through my dialup modem on my laptop (here in Indiana, there are still wide swaths of land without a bloody high speed connection in sight - am currently living in such a place, and even though I'm set to move back to civilization in the next couple of months, I'd like to have it available just in case).

Got the driver from Linuxant (yeah, it's one of THOSE...), installed and configured it, installed gnome-ppp and configured that, and started dialing. 

Both in wvdial and gnome-ppp, the modem dials out fine and the log shows no problems. When I open Firefox, my start page is loaded...

However, after a maximum of about 10 seconds, the connection does not work anymore (which does not show up in a log and also does not result in disconnection) - pages simply stop loading. I changed the start page to other URLS - those would load (sometimes partially, if the site is big), but nothing afterwards. If I'm fast, I can get one other page to load halfway after the start page, but then the connection dies on me again. GAIM does not connect whatsoever.

I went through [this]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6") howto with a fine-toothed comb - yes, I did comment out lcp-echo-interval30 and lcp-echo-failure4, and I added replacedefaultroute. I have tried changing options such as Carrier Check and Stupid Mode. The problem persists.

I am using Ubuntu 6.06 LTS (I know, probably the worst choice for getting dialup to work - but hey! It actually likes my BCM4318, curiously enough! :) ), my computer is a HP Pavilion ze2308wm.

Thank you very much in advance for any advice you can give me!

---

### Post by tweakbox on 2007-08-06
have you tried pppconfig and editing /etc/ppp/peer/provider that should help.scripts and files are pretty self explanatory

---

