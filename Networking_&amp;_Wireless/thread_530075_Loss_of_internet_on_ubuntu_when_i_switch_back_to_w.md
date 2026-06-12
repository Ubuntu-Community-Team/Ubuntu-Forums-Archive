---
title: "Loss of internet on ubuntu when i switch back to winxp"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by Perplexingman on 2007-08-20
I am still new to ubuntu and have installed it twice and have through alot of reading fixed most of my problems. However this one i can not figure out. I have a separate hard drive devoted to learning about linux first off i could get nothing to work right so i installed winxp and then copied over completely with ubuntu. This allowed me to gain internet through my provider through a dchp. Here is the problem though if i reboot and go to my main hard drive the one with win xp and then return later to ubuntu i can no longer get on the internet even though it says that i am connected to a wired network i have tried to switch to static ip and added all the info correctly but to no avail. Can anyone please help me? I am sure someone has had a similar problem. If i can not have internet on ubuntu then there is no point in messing with it or linux anymore. thanks in advance for any help you can give

---

### Post by will71110 on 2007-08-20
Try unplugging your NIC while you reboot.  Newer NICs usually stays online even if the computer is off (WOL Wake Online is usally why it stays).  Or you can disable WOL in BIOS.

---

### Post by Perplexingman on 2007-08-20
Ok i could not find WOL in the bios and i unplugged my modem and rebooted but still have no luck. When i first had the internet on ubuntu there was no  problem if i rebooted back to ubuntu however the moment i oot into winxp i no longer can obtain my internet on ubuntu. It' s frustrating i have had several problems and thankfully through reading these forums i have fixed them all but this one. Thanks in advance for any help you may give

---

### Post by will71110 on 2007-08-20
Are you using a modem directly plugged into the computer or does this come off a NIC buecause you said "unplugged the modem".  If its a USB modem then might be something to do with the USB then.

Anyways let me know which you are using.

---

### Post by Perplexingman on 2007-08-20
modem is a westell plugged directrly int the computer via ethernet cable. i have spent the past hours trying everything i can find and have yet to come up with a fix.

---

