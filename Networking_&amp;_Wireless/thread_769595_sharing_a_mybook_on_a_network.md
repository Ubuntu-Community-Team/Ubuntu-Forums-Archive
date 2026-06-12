---
title: "sharing a mybook on a network"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by jmulder19 on 2008-04-26
hi everyone i need some help :( i can't access my mybook on my network between 2 ubuntu computers:(

---

### Post by FrankT-Qc on 2009-04-21
What have you tried as a mean of sharing ???

From the absence of details, I guess you have not tried allot and I'll guess your running Intrepid Desktop...

If you navigate to /media you'll see that there is a folder associated with your external drive. You could right click it and select "Sharing Options"

From there, you check "Share this folder", give the share a name Let's say MyBook-01 ... You might want to make sure you don't allow guest access unless you're in a really safe environment. If you don't you'll have to provide your username and password to remotely access the drive, the same login and password you use to log on the machine that has the drive plugged in.

From the other machine, you'll go into the "Places" menu (besides "Applications" and select Network.

Try this and if it still doesn't work, you can try connection via smbclient and try increasing verbosity until you have enough detail to figure out what's wrong.

---

