---
title: "Network connetivity issue"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by Chayak on 2006-11-04
This is probably one of the more unique problems I've had with linux.  My dell XPS has been working great but lately after I leave it for a while and come back I have no network connectivity and have to bring eth0 down and back up to get it back.  I'm running a static IP and this is confusing me quite a bit.  Has anyone else seen this?

---

### Post by louistan3 on 2006-11-05
this happens to me too.. i duno if we have the same problem but when i leave my laptop on.. when i get back my internet wont work anymore.. even when im downloading with azureus.. it just stops working and id have to bring my eth0 down and up again for it to work.. does any1 have a fix for this? :-S

---

### Post by louistan3 on 2006-11-08
i think i fixed my problem.. i have a marvell yukon card.. the current module that it uses has bugs.. so i just installed the older one..

 what is your ethernet card? maybe youve got the same card as me..

try doing this in the terminal
```
lspci | grep eth
```

---

