---
title: "Sharing files and network attached storage with windows2000 network"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-07-30
okay, i have a fairly complicated issue that i'm not sure how to resolve.

current network setup is with a win2000 server.  this server currently has a dinosaur of a 7gig network attached storage unit (currently attached to the win2000 server via parallel cable ... yes really freaking slow).

i have built an 80gig ubuntu samba server machine with raid1 as a replacement for our puny network attached storage unit.  and i need to figure out how to make the transition go as seamless as possible.

in order to accomplish this, i want to make the ubuntu server storage available to the network via the win2000 server rather than directly from the ubuntu server.

anyone have any idea of how something like this can be done?  networking is not a particular strength of mine.

---

### Post by OpsVentus on 2006-07-31
1 You have to share the disk via Samba to the win2000 server.
2 Connect the win2000 server to the Ubuntu Samba server.
3 Share the disk on the win2000 server in the way you do the other disk now.

1 See where the disk is mounted now, right click in Nautilus and click "share folder". Set to Samba.

2 In Explorer go: \\[ip-adres ubuntu]. Right click folder, click "connect"(or something like this, not exactally shure).

3 Right click drive, click "settings", share like you have shared the other one.

Cheers,
Bart.

---

### Post by dmizer on 2006-07-31
actually the network attached storage is a headless/gui-less server only install of ubuntu so i have no "click" options.  but that's beside the point.  i was able to share the folders across the network no problem.

i can even get the win2000 server to mount the ubuntu samba shares no problem, but win2000 can't share a share.  it is simply not possible to do so.

---

### Post by crmanski on 2006-07-31
I was wondering how the clients machines attach to the win2k server? and how? Are you using a domain/active directory to store the account information? Or is the server a standalone server (Workgroup)?

---

### Post by dmizer on 2006-08-01
at this time both the network attached storage ubuntu samba file server and the win2000 server are netbios.#-o

everything except the network attached storage server, and the win2000 server runs through a router directly to two hubs (no, not switches ... hubs). 

there are roughly 20 clients in service on my network, but only about half get hard use.

i gave consideration to rolling everything over to the ubuntu server, but currently the win2000 machine is serving up printers.  printers that do not have cups drivers (no really, they don't exist).  perhaps in the future, i can install a dedicated network print switch, but that's out of the budget at this time.:rolleyes: 

there's also a small matter of ftp clients which i've yet to be able to glean the functionality/configuration of.

i'd also like to eventually move everything to AD, but that's beyond my abilities at this point. :-(  (anyone know of some good ubuntu based AD tutorials?)

this beast of a network just recently got dumped in my lap and i'm trying to correct years of neglect.  first thing i had to address though was the fact that network storage was at critical mass.

---

### Post by OpsVentus on 2006-08-02
Well there's a lot of fun for you ahead then!

I think it's possible to share a share in Windows2000, but that's Microsoft territory and there are a lot of other forums to handle that stuff.
But you can also set the clients to use the Ubuntu server directly.
If you got a domain running, it's just a few clicks on the server.

Cheers,
Bart.

---

### Post by OpsVentus on 2006-08-02
Well there's a lot of fun for you ahead then!

I think it's possible to share a share in Windows2000, but that's Microsoft territory and there are a lot of other forums to handle that stuff.
But you can also set the clients to use the Ubuntu server directly.
If you got a domain running, it's just a few clicks on the server.

Cheers,
Bart.

---

### Post by dmizer on 2006-08-02
well, frankly that's what i did finally end up doing. i was hoping to avoid it because i knew it was going to mean me configuring every box (win98, winNT, win2000, and xp) in the office by myself ... in japanese (which is not my native language).

anyway ... thanks for all the advice.

---

