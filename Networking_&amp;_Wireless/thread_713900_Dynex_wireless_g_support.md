---
title: "Dynex wireless g support"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by tallguy62 on 2008-03-03
Im brand new to Linux/Ubuntu in general. im trying to find drivers for my wireless card  ([http://www.dynexproducts.com/pc-595-4-dynex-80211g-enhanced-wireless-g-desktop-card.aspx](http://www.dynexproducts.com/pc-595-4-dynex-80211g-enhanced-wireless-g-desktop-card.aspx))
and i cant seem to find any, plus i don't know if my card is even supported?(currently not on my Ubuntu machine will be later after school)
where would I look when for compatibility and drivers for the card?

---

### Post by rustybronco on 2008-03-03
Should work fine out of the box. 
this is the card that I use in  my desktop. [http://ubuntuhcl.org/browse/product?id=110](http://ubuntuhcl.org/browse/product?id=110)
sorry new computers here at work and i.e wanted to to know if I wanted to save the file for this link 

it now has firefox on it.

***edit*** the model number is different than the one I have, but they repackaged that card so it may have the same or a different chipset than mine.
no matter we'll help you get it up and running if needed.

---

### Post by tallguy62 on 2008-03-07
> **rustybronco said:**
> Should work fine out of the box. 
this is the card that I use in  my desktop. [http://ubuntuhcl.org/browse/product?id=110](http://ubuntuhcl.org/browse/product?id=110)
sorry new computers here at work and i.e wanted to to know if I wanted to save the file for this link 

it now has firefox on it.

***edit*** the model number is different than the one I have, but they repackaged that card so it may have the same or a different chipset than mine.
no matter we'll help you get it up and running if needed.


Well im back and I tried to go to driveguide.com but i found out that ubuntu 7.10 does not recognize exe files so im SOL 

can anyone help me?

---

### Post by rustybronco on 2008-03-07
> **tallguy62 said:**
> but i found out that ubuntu 7.10 does not recognize exe files so im SOL 
can anyone help me?.exe files are for windows, you are in a different world... un-learn it.
> so im SOL said who?
open the terminal and post the output of **lspci -nn** and ** iwlist scan**

---

### Post by tallguy62 on 2008-03-07
> **rustybronco said:**
> .exe files are for windows, you are in a different world... un-learn it.
 said who?
open the terminal and post the output of **lspci -nn** and ** iwlist scan**

ok so i uploaded the document
what now?

---

### Post by rustybronco on 2008-03-07
this is the chipset for your card.
> 
02:07.0 Network controller: Broadcom Corporation **BCM4318 [AirForce One 54g]** 802.11g Wireless LAN Controller (rev 02)

[http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)

---

### Post by tallguy62 on 2008-03-07
> **rustybronco said:**
> this is the chipset for your card.


[http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)


ok i followed your exact directions and for some reason it keeps coming back telling me that the drivers are not enabled.:confused:
edit: got the lan the video working, still tinkering with the wireless
youve been a major help thanks alot

---

### Post by rustybronco on 2008-03-07
> **tallguy62 said:**
> ok i followed your exact directions and for some reason it keeps coming back telling me that the drivers are not enabled.:confused:
edit: got the lan the video working, still tinkering with the wireless
youve been a major help thanks alotsometimes it requires a restart.
let me know if I can help.

---

### Post by tallguy62 on 2008-03-07
> **rustybronco said:**
> sometimes it requires a restart.
let me know if I can help.

i restarted and still the wireless wont work
so i start meh search via Google.....any suggestions where to start?

edit: its saying something like "bcm43xx-fwcutter" is not enabled
whats that?

---

### Post by rustybronco on 2008-03-07
did you enable the software sources?

also  [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

> edit: its saying something like "bcm43xx-fwcutter" is not enabled
whats that? bcm43xx is the driver for your card.

---

### Post by tallguy62 on 2008-03-07
> **rustybronco said:**
> did you enable the software sources?

also  [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)


yes
now im having video driver problems!!!
grr!! ubuntu +newbie=driver hell!!
but your help has been:KS-worthy

---

### Post by rustybronco on 2008-03-07
> VGA compatible controller: nVidia Corporation G70 [**GeForce 7800 GS**] (rev a2)

go to the multimedia&video section of this forum and search/ask for help with your card.
then come back and we'll have a go at it in depth.

---

### Post by tallguy62 on 2008-03-07
> **rustybronco said:**
> go to the multimedia&video section of this forum and search/ask for help with your card.
then come back and we'll have a go at it in depth.

i made the ULTIMATE newbie mistake
it was so obvious!
i didnt really install ubuntu i was running off the live cd!!
so yea once i installed i fixed all my updates/driver probs and yea now im bored with it
lol....im a moron....lol
thanks alot for the patience and the help tho

---

### Post by rustybronco on 2008-03-07
Would not have figured out that reason for a while. ;)
Your welcome, glad to have you aboard.

---

