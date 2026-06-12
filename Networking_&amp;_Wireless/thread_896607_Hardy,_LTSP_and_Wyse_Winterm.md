---
title: "Hardy, LTSP and Wyse Winterm"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Bill259 on 2008-08-21
Hi all,

I've had a trawl through the forums for this question but can't see anything that really helps me.  Apologies if this has been asked before.

I set up Hardy with LTSP last night, stunningly simple (*), set my HP laptop (WinXP home on it) to PXE boot, it connected first time, loaded a desktop, allowed me to log in, and everything worked swimmingly.

I've a number of Wyse WinTerm 3150SE machines that I'd like to be able to use. They're capable of PXE boot and the first one I plugged in connected ok, did the cylon thing briefly, then displayed the ubuntu load screen and the progress bar filling from left to right. It stopped five blocks from the right. Nothing else happens. 

Will this ever work and if so what am I doing wrong? I've seen some forum entries for replacing the WinCE OS on the WinTerm with linux but I thought that PXE pretty much ignored the installed OS and got on with it. I don't want to go through reflashing the WinTerms.

Any help thankfully received, even if it isn't good news.

TIA,
Bill.

(*) once I'd figured out that the install sets the thin-client network up with 192.168.0.1 as its IP address, which was the same as my Netgear switch.

---

