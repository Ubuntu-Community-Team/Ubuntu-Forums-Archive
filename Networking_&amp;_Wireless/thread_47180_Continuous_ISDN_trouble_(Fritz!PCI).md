---
title: "Continuous ISDN trouble (Fritz!PCI)"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by cwkx on 2005-07-07
Edited: Uhh, sorry this was posted in the wrong place - clicked Warty Warhog instead of Hoary Hedghog, reposted in the correct place!  #-o 

Hi all, I've been having repeated problems trying to get my ISDN card to work, to find out what it was and whether it was compatible I ran: [FONT=Courier New]sudo lspci -v[/FONT] and it said it was a "0000:00:0b.0 Network controller:AVM Audovisuelles MKTG & Computer System GmbH Fritz!PCI v2.0 ISDN (rev 01)" 

I followed the IsdnHowto at: [https://wiki.ubuntu.com/IsdnHowto?highlight=%28ISDN%29](https://wiki.ubuntu.com/IsdnHowto?highlight=%28ISDN%29)

and when at the last stage, after typing:
[FONT=Courier New]$pon isdn-wanadoo [/FONT](wanadoo being the name of my set-up provider)

here is a dump of what occured:
[FONT=Courier New]Plugin userpass.so loaded.
userpass $Revision: 1.5 $
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn: 1.10
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)]
[/FONT]

I am quite sure that I have installed all the CAPI packages correctly as the guide stated though. Any ideas?


PS, Sorry for my first post being such a question!  ;-)

---

### Post by sigge on 2006-01-05
This problem seem to me to be caused by capi not being configured....

I derive this from reading the man-pages of capiinfo and capiinit, one of wich clearly states that capiinit looks for its configuration in /etc/isdn/capi.conf

This is where I halt...  capi.conf contains a lot of commented (#) driver suggestions, that one presumably should uncomment according to wich card one has. But it is in no way clear how this should happen, or what the different commented lines corresponds to.

This problem is starting to annoy me. It's nobodys fault.... It just does. For two days now, I have been working With this Eicon Diva ISDN ISA 2.01 card. For the better part of yesterday, I was struggeling with finding out why ubuntu insisted that 
> capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)] 


:confused: I wish I knew the capi.conf configuration parameters. Does anyone know where to find them?
Better yet, has anyone configures said card, (Eicon Diva ISDN ISA 2.01) in breezy? This is important, as I'm really stuck here. I'm trying to migrate this doctors office from win2k to linux, and thought that ubuntu would be best. For everything except the isdn thing, I was right. But then again, the doctor dude doesn't find his soundcard mission critical... The isdn on the other hand... Well...

Eternally gratefull for your response.

---

