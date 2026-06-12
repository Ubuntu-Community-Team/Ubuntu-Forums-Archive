---
title: "Continuous ISDN trouble (Fritz!PCI)"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by cwkx on 2005-07-07
Hi all, I've been having repeated problems trying to get my ISDN card to work, to find out what it was and whether it was compatible I ran: [FONT=Courier New]sudo lspci -v[/FONT] and it said it was a "0000:00:0b.0 Network controller:AVM Audovisuelles MKTG & Computer System GmbH Fritz!PCI v2.0 ISDN (rev 01)"

I followed the IsdnHowto at: [https://wiki.ubuntu.com/IsdnHowto?highlight=%28ISDN%29](https://wiki.ubuntu.com/IsdnHowto?highlight=%28ISDN%29)

and when at the last stage, after typing:
[FONT=Courier New]$pon isdn-wanadoo[/FONT] (wanadoo being the name of my set-up provider)

here is a dump of what occured:
[FONT=Courier New]Plugin userpass.so loaded.
userpass $Revision: 1.5 $
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn: 1.10
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)][/FONT]


I am quite sure that I have installed all the CAPI packages correctly as the guide stated though. Any ideas?

PS, Sorry for my first post being such a question!  ;-)

---

