---
title: "Samba - &quot;Parameter is incorrect&quot; Can't browse samba server"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by floz23 on 2007-09-27
Hello,

I can not browse my samba server, the shares work fine.  For instance, I can specify \\server\share1 perfectly, and the printer server works great!  But, when i try to browse the samba server via "View Workgroup Computer" in windows xp, it get an error "The Parameter is incorrect."

Afaik, my users are all setup properly, and have no problems doing anything except browsing the server!

I noticed something kinda odd, in my list of workgroup computers, I see listed at the name of the server 

sambaserver (SAMBASERVER\sambaserver)

While my windows machines are listed:

winbox (descriptionOfTheMachine)

Can anyone help?

-Adam

---

### Post by floz23 on 2007-09-27
Ok, I solved my own problem, after playing with the .conf and restarting the daemon a bunch of times, lol.

But anyway this is what I added to my samba.conf, I thought I had originally added these, but i guess not.

username map = /etc/samba/smbusers
netbios name = YOUR_HOSTNAME

---

