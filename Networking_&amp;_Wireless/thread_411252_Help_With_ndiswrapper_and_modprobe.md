---
title: "Help With ndiswrapper and modprobe"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by windrider621 on 2007-04-16
I've been having problems with me wireless setup, but managed to get most of the problems sorted out. However, when I try "sudo modprobe ndiswrapper" I get the FATAL error message along the lines of "module ndiswrapper could not be found." Since I have no wire internet hook-up I can't get the exact error message, but its close to that.

Anyone else deal with this before? Thanks for any help.

---

### Post by nautilus on 2007-04-16
sure, which kernel are you running? uname -a

and the version of ndiswrapper? ndiswrapper -v

does `sudo depmod -v|grep ndiswrapper` say anything interesting?

---

### Post by windrider621 on 2007-04-16
I'm running 2.6.17-10-generic. I can give you the rest of the uname-a output if needed, but that seems to be the important stuff. I think the ndiswrapper -v showed the main problem, it gives me:

"utils Error: no version specified!
driver modinfo: could not find module ndiswrapper"

Someone suggested that I install a newer version of ndiswrapper earlier, but I wasn't succesful in doing so when I tried. Perhaps that would fix it if someone could help me figure out what I did wrong? Or maybe something else will fix it.

Aso the last command gave no output, but I wasn't too worried for now, since it looks like I've found the root of the problem.

---

### Post by windrider621 on 2007-04-18
Is there anyone who can help me fix the problem with ndiswrapper or help me install a new version that will work?

---

### Post by windrider621 on 2007-04-18
Sorry to post again so soon, but I noticed that the new version of Ubuntu is realeased tomorrow. Is it dificult to start over with Fiesty? Perhaps I'd have better luck with Fiesty, since that would come with a newer ndiswrapper (I'd guess). Or should I just try and fix it with my current version and then update to Fiesty? I know this doesn't directly relate to networking, but switching over tomorrow (or this weekend) would be primarily to help get my network set up. Thanks for your advice/oppinions.

---

### Post by windrider621 on 2007-04-20
Anyone?

---

