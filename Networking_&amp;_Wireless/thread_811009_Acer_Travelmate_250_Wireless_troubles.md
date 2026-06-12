---
title: "Acer Travelmate 250 Wireless troubles"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by the_flood502 on 2008-05-28
Howdy... 

i'm having some difficulty getting my wireless internet connection to appear on my Acer Travelmate 250...


no wireless connections appear on the wireless seach thing... 


I'm running Ubuntu 7.04 

i think it might be the wrong drivers or something

>  Re: Fiesty 7.04 wireless, working for you or not ?
My experience is that depending on what driver your wireless is using a kernel upgrade may or may not break it...lol...and what might work for one may not work for another. That said, I have an Acer Travelmate 250, that was upgraded from 6.10 to 7.04. The laptop has a built-in wavelan wireless adapter that is based on the prism 2.5 chipset, at least from what I gather by reading the various posts. ANYway, the card actually uses the orinoco driver and in order to get mine to work i had to add the following entries to my blacklist file:

blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

Your mileage may vary, good luck!

i found this post on the forum after some searching... but i have NO idea what a 'backlist' file is =(

help please?


Thanks

Dean

---

