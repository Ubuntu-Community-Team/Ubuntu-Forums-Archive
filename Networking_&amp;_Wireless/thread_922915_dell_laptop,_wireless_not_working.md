---
title: "dell laptop, wireless not working"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by compl3te_newbie on 2008-09-17
help [-o<

broadcom 440x10/100 integrated controller
dell wireless 1395 wlan mini card


hi, i have a dell inspiron 1721 laptop. i am currently connecting to the internet via an ethernet cable when using ubuntu. finally i (honestly i think it just decided to start working by itself....or i just dont know what i did:lolflag:) got ubuntu to recognize my wireless card. when i have wireless enabled  & select my router's network from the drop down it asks for my paraphrase (naturally) i enter it and ensure that the correct security thingy (wpa, wpa2 etc.) is selected and hit connect. the network status icon changes to little status bars indicating my connection strength, the problem is when this happens even though it shows 100% connection to the network firefox will not connect to any webpage.:confused:  not sure wats going on. when i disable wireless and revert back to the ethernet cable firefox connects fine. oh and here is hardware info:

              
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
      
also in windows device manager it says 
broadcom 440x10/100 integrated controller
dell wireless 1395 wlan mini card

thanks for any help/suggestions

---

### Post by funkydan2 on 2008-09-18
When you're connected via wireless have you tried to ping any servers?  Either by their name (e.g. ping ubuntu.com) or their IP address (e.g. ping 91.189.94.249)?  (You do this by opening up a terminal window and typing the command in at the prompt.)

If you do this, what happens?

Maybe should also post the output of 'ifconfig' (once again, type it at the terminal) here so that someone can see what all the settings are.

(You could do all these things through various point and click tools, but its easier to use the command prompt, because then you can just copy and paste the output here rather than either taking screenshots or trying to describe what's on the screen.)

---

