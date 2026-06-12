---
title: "Dv8000 wifi switch problem"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by sconnyuk on 2011-07-25
Hi, very new to Ubunutu forums and on top of that very new to Ubuntu. Straight to the point, ive searched all day trying to fix my issue but still cant seem to find out how to fix it. So ive had to give in and ask on here for help. Ive a HP DV8000, well actually the exact make of it is dv8263ea. I have just installed Ubuntu 11.04 on it and when it was installing i had my ethernet cable plugged in to let it download updates for me while it installed, as it did not pick my wifi up. Now after trawling lots of posts on various sites ive recognised my wifi card is an intel pro wireless 3945abg card installed, But im unsure if the correct driver is installed, on top of that the wifi light right in the top centre above my keyboard will not switch on when i press the button. If there is anyone who has had this issue before or knows how to fix it can help i will be very grateful, as i do not want to go back to a windows machine as i very much like ubuntu, ive got it installed on my desktop and runs very good. Thanks in advance.

---

### Post by carverj on 2011-07-26
Seems to be supported as of earlier Ubuntu OS: -
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)
So does this machines wifi work with other operating systems?

---

### Post by wildmanne39 on 2011-07-26
Hi, run these commands in a terminal please.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
 and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by androssofer on 2011-07-26
```
on top of that the wifi light right in the top centre above my keyboard will not switch on when i press the button
```

wudnt worry about tht, my wifi light had a mind of its own under ubuntu...

---

