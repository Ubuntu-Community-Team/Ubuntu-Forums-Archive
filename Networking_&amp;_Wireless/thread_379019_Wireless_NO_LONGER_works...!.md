---
title: "Wireless NO LONGER works...?!"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by drsaamah on 2007-03-08
Okay, I've been using Ubuntu for three or four weeks now, I think, and it's been going great until today (well technically yesterday).  I've been using Wi-fi and all was good and dandy, until about 4.5 hours ago I turn on my laptop and I can no longer connect to any wireless networks.  I have walked around town trying to connect to two Wi-fi sources, as well as my universities and nothing works anymore.
The weird thing is it *says* I'm connected (under connection properties it gives me a >90% signal strength), but under "activity" it says it has recieved no packets.  I know my wireless key and network name are right.  What can possibly be wrong?
I have Wi-fi radar installed and use that frequently.  Could that have done something to my network connections without me knowing?  Someone help me!

---

### Post by drsaamah on 2007-03-08
btw, I know I haven't given any solid information but I'm still very scetchy on the terminal so please let me know what is needed (and the shell commands required to get that info) and Ill be sure to post it!
Thanks to all potential helpers!

---

### Post by drsaamah on 2007-03-08
okay...guess I'm giving up and going to bed for tonight...
someone please help me or point me in the right direction when you get the time.
:( 
sad without my wi-fi...

---

### Post by hardyn on 2007-03-08
ive started to have some network trouble as we... past few days...
although im using networkmanager and ipw2200...

did an update happen in that time?

wonder if something got broke?

---

### Post by axcairns on 2007-03-08
My Aironet 350 stopped working a few days ago after running flawlessly for years. 

hhhmmmmm

Allan

---

### Post by Jsgrabo on 2007-03-08
One thing you could check on is in the system>administration>networking menu. My ethernet connection is labeld eth0 and my wireless is wlan0. under Default Gateway Device, make sure that your wireless device is selected. somehow it got changed on my laptop to my ethernet device, which wasnt connected, and it said that i was connected to my wireless network but i wasnt getting to the internet. i switched it back to my wireless card and i was back in business.

---

### Post by aberry5555 on 2007-03-08
did you by any chance do any updates that day? If you're using ndiswrapper for your card then it will have broken because of a kernel change. If this is the reason do a complete uninstall then reinstall of ndiswrapper (hopefully it was done from the repositories :S) then reconfigure it and, fingers crossed, that should help.

---

### Post by axcairns on 2007-03-08
> **Jsgrabo said:**
> One thing you could check on is in the system>administration>networking menu. My ethernet connection is labeld eth0 and my wireless is wlan0. under Default Gateway Device, make sure that your wireless device is selected. somehow it got changed on my laptop to my ethernet device, which wasnt connected, and it said that i was connected to my wireless network but i wasnt getting to the internet. i switched it back to my wireless card and i was back in business.

How is the default device defined under feisty? I can see nothing in the Network Settings dialog that controls this.

Thanks,


Allan

---

### Post by axcairns on 2007-03-08
> **aberry5555 said:**
> did you by any chance do any updates that day? If you're using ndiswrapper for your card then it will have broken because of a kernel change. If this is the reason do a complete uninstall then reinstall of ndiswrapper (hopefully it was done from the repositories :S) then reconfigure it and, fingers crossed, that should help.

Very possible yes but I am not using ndiswrapper. My card is(was) supported by the airo_cs driver which is part of the stock kernel.

Thanks,

Allan

---

### Post by drsaamah on 2007-03-08
> **Jsgrabo said:**
> One thing you could check on is in the system>administration>networking menu. My ethernet connection is labeld eth0 and my wireless is wlan0. under Default Gateway Device, make sure that your wireless device is selected. somehow it got changed on my laptop to my ethernet device, which wasnt connected, and it said that i was connected to my wireless network but i wasnt getting to the internet. i switched it back to my wireless card and i was back in business.

Nope.  My ethernet connection is completely disabled because I use nothing but wi-fi!!




> **aberry5555 said:**
> did you by any chance do any updates that day? If you're using ndiswrapper for your card then it will have broken because of a kernel change. If this is the reason do a complete uninstall then reinstall of ndiswrapper (hopefully it was done from the repositories :S) then reconfigure it and, fingers crossed, that should help.

Nope didn't do any updates that day either.  And I'm not using ndiswrapper!  I don't know what could have possibly happened.  And other ideas, anyone?

---

### Post by drsaamah on 2007-03-08
wait a minute now...
Under the "networking" menu it has a check by "Wireless connection" and NO CHECK by "wired connection", which is why I said that I was using my Wi-fi.  However, When I right click on the Wi-Fi icon up by my clock, and click "Properties" and then click on the "Support" tab, it says the "type" of my connection, is "Ethernet".  I don't even have a cable going to my computer!!
:(

---

### Post by hardyn on 2007-03-08
i noticed that too... im wondering if network-manager behaves like this?

---

### Post by drsaamah on 2007-03-08
I dont know, but I don't use network manager, I use wi-fi radar.  Anyways forget me...my internet is working now...somehow.  I guess Ubuntu is self-healing :)

---

### Post by hardyn on 2007-03-08
post back here when it breaks again... its sounding alot like my current problem...

its sounding like their might be something going on.

---

### Post by drsaamah on 2007-03-09
hahah...okay NOT fixed.  I guess it's only on my my school's wi-fi and at the local ben n jerrys wi-fi it doesnt work.  Everywhere (seemingly) its fine.  I can't think of what characteristic distinguishes those two services from the others...
Does this sound like a problem that ANYBODY has ever heard of before??  I'm dying out here guys...

---

