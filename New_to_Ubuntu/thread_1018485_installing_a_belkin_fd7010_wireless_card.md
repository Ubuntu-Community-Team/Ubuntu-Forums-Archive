---
title: "installing a belkin fd7010 wireless card"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by chrjacks on 2008-12-22
hi everyone. need some help. i'm a newbie so go easy and make stuff simple.

i think i've installed the wireless modem but now its not recognizing as wlan in network tools. i used ndiswrapper and everything looks fine until it doesnt come up as a wlan.

any help? if you need the results of some commands, let me know.

thanks

---

### Post by mikeyphi on 2008-12-22
Welcome!
Depends on exactly which chipset is in your card!
To determine what wireless card/chipset you have, open up a terminal and type the following.

lspci -v | less

Then, scroll to find your wireless device and note down its details.

Then see what you should do here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

remember, if you're using ndiswrapper, you also need the windows driver.

If it still doesn't work - give us ALL the details!

---

### Post by chrjacks on 2008-12-22
ok i have the driver installed using ndiswrapper. 

its a belkin f5d7010 v.4 pc card wireless adapter. 

when i put ndiswrapper -l into terminal i get:
bcmwl5 : driver installed
       device (14E4:4318 ) present (alternate driver: ssb)

its just that once i go to system > administration > network tools  there is no wlan present. any thoughts?

---

### Post by chrjacks on 2008-12-22
if it makes any difference, the lights on the wireless adapter arent even turning on

---

### Post by mikeyphi on 2008-12-23
A suggestion - try the bcm43xx-fwcutter option:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Remember to uninstall ndiswrapper first.
If that doesn't work for you - reinstall the windows driver using ndiswrapper-utils

Sorry - I can't think of anything else.
But, if necessary, do ask again, perhaps under the 'Networking & Wireless Forum'

---

