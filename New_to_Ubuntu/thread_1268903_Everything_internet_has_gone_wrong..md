---
title: "Everything internet has gone wrong."
date: 2009-09-17
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-09-17
Hello, first my wireless internet died. I got alot of help on the fourms to fix it and it worked, a week later i updated again and it knocked my wireless off again used the same method as before and it still didnt work. i was told to use the Have a look at /etc/NetworkManager/nm-system-settings.conf, it should look like this:


Code:
cat nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:16:17:9c:84:b5,

[ifupdown]
managed=falseChange the managed=false to managed=true, then reboot.

This method and on the terminal i got "permission denied"  and i look at my shortcut bar where my little wireless bars and and they are gone. What the hell?
Super pissed off right now. I needed to get this fixed as soon as and its just all went wrong.

---

### Post by LewRockwell on 2009-09-17
upgrade with a fresh install of 9.04

.

---

### Post by Rave Gloves on 2009-09-17
> **LewRockwell said:**
> upgrade with a fresh install of 9.04

.

Could you tell me how i should go about this?, will i need to use my Install disk again?


Edit, Sorry i forgot to mention that i have 9.04

---

### Post by LewRockwell on 2009-09-17
> **Rave Gloves said:**
> Could you tell me how i should go about this?, will i need to use my Install disk again?


Edit, Sorry i forgot to mention that i have 9.04

wifi has been problematic for some people since 8.04 and 8.10

we've had much better experience with 9.04 but there are still issues

we've been having to reset cable modems, routers, and computers

also make sure your browser caches, cookies, and other temp. data are all deleted

oh, and check out "betterprivacy" addon for firefox to get rid of those secret flash cookies!

(can't stand all that garbage...lol)

.

---

### Post by Rave Gloves on 2009-09-17
> **LewRockwell said:**
> wifi has been problematic for some people since 8.04 and 8.10

we've had much better experience with 9.04 but there are still issues

we've been having to reset cable modems, routers, and computers

also make sure your browser caches, cookies, and other temp. data are all deleted

oh, and check out "betterprivacy" addon for firefox to get rid of those secret flash cookies!

(can't stand all that garbage...lol)

.

See when i re install my ubuntu, is there any way i can update it without updating my wifi drivers? that is my only moan of this os i share the wifi pain, i have tried ubuntu several times in the past and this is the reason i never stick with it!

---

