---
title: "vpnc error"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by dannemil on 2007-05-18
I keep getting the following error when I try to run vpnc-connect

vpnc-connect: binding to 0.0.0.0:500: Address already in use

Can anybody help me out here and resolve this error?

Thanks, Jim

---

### Post by javahollic on 2007-05-22
Same here, just hit this today.  A collegue uses the exact same software stack, at it works for him.  I wonder if it relates to bridging and wireless access somehow? He uses wired connections whereas I have wireless.  In theory no difference, but If I figure it out Ill post back.

Google only gave me this thread so its got to be something whacky...

---

### Post by felipebm on 2008-02-07
are you sure you dont have any other idle vpnc connections ?

try these:

#sudo vpnc-disconnect
#sudo killalll vpnc

and then try to connect again.

---

