---
title: "samba server not working please help"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by seepage87 on 2007-12-18
I recently built a file server (currently running a full gutsy install, though) for my house (everyone but be is only somewhat computer literate) and used [this guide]("http://www.debuntu.org/guest-file-sharing-with-samba") to get samba running so that all of them can access the shared folder from their windows machines as a network drive.  

Everything was working fine until I rebooted my server.  This morning I couldn't access the shared drive from my windows box, either by \\computername or by \\ip.ad.dre.ss as I could before.

I'm still sorta new to this whole thing, so I was wondering,  is something missing from that guide to get it working on boot, such as changing the init.d samba script or something?  How would I fix it?  I've never really done much of this before, though I'm relatively comfortable in the terminal when I have instruction.

Thanks

---

### Post by HermanAB on 2007-12-18
Run 'ps -e' to see whether 'smbd' and 'nmbd' are running.

Also see this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

