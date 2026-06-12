---
title: "X window to Solaris 9"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by PaulHuffman on 2008-03-27
I just upgraded from 7.04 to 7.10.  Today I had a need to open up an X session from 7.10 to my old Sun Ultra 10 running Solaris 9, but I couldn't figure it out.  I could rlogin to the Solaris machine. At a terminal window on 7.10, I tried adding the solaris box as an xhost, rlogin to Solaris, set the display back to the ubuntu box, and kicked off some x apps like xclock on Solaris, but they didn't find their way to the unbuntu screen. 

What's this "Terminal Server Client" app on unbuntu? I couldn't find anything on it in the user docs.   I found my old VNC server software on the Solaris box and started that up, but TSC couldn't connect to it with its VNC protocol.  Is my VNC on the Solaris box too old (3.3.3v2)? I tried TSC's XDMCP but couldn't get that to work either.  I verified that I can still make a XDMCP connection to this Solaris box with Reflection X on an XP.

---

### Post by PaulHuffman on 2008-03-27
I finally figured out that vncserver on the Solaris box started up display 1.  Then VNC or TSC with VNC protocol would hook up if I specied host by name or IP with :1 after it.  I don't know why display 0 didn't start up. 

Still no luck with XDMCP.

---

