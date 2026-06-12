---
title: "wireless weak"
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2005-09-09
my wireless signal on Ubuntu is weak, and drops out time to time...

I held my laptop up to the router, and the best it got was 90%...  when booted in Windows, the signal is 100% throughout the house (unless I go out back, then it goes to 80%)...  and on Windows, the signal don't drop out...

what's going on Ubuntu?  it's one of those AT&T cards, the 6500 and a 6700 (two computers have the same problem)...

---

### Post by seethru on 2005-09-09
[QUOTE=X5-655]my wireless signal on Ubuntu is weak, and drops out time to time...

I held my laptop up to the router, and the best it got was 90%...  when booted in Windows, the signal is 100% throughout the house (unless I go out back, then it goes to 80%)...  and on Windows, the signal don't drop out...

what's going on Ubuntu?  it's one of those AT&T cards, the 6500 and a 6700 (two computers have the same problem)...[/QUOTE]
 what chipset? are you using ndiswrapper?

---

### Post by X5-655 on 2005-09-09
[QUOTE=seethru]what chipset? are you using ndiswrapper?[/QUOTE]
i don't know what chipset, all I know is that the model number on the desktop PCI card and laptop card are 6500 and 6700..

also, how do I know if I am using ndiswrapper?  im very new to using linux....

all i did to get the card working was put it in, selected my network, entered the key, and selected "ath0" as the default gateway..

---

### Post by seethru on 2005-09-09
[QUOTE=X5-655]i don't know what chipset, all I know is that the model number on the desktop PCI card and laptop card are 6500 and 6700..

also, how do I know if I am using ndiswrapper?  im very new to using linux....

all i did to get the card working was put it in, selected my network, entered the key, and selected "ath0" as the default gateway..[/QUOTE]

see if you can find your chipset [here](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) and find information regarding ndiswrapper (not neccessarily needed, depends on the chipset) [here](http://ndiswrapper.sourceforge.net/)

---

