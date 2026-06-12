---
title: "firestarter rules not working"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by Epica on 2006-12-29
I am running a old desktop computer with an edgy server install and want to use it as a headless server. I am using XDMCP and SSH to remotely administer it and I am also using CUPS to share a printer with IPP. I have set up the nesessary firewall rules using firestarter

allowing the following ports for everyone in my inbound traffic policy 177 for XDMCP, 6000-6015 for X-windows, 177 for XDMCP to listen on, 631 for IPP and 2256 for SSH.

Can anyone point me in the right direction? I know that Ubuntu should boot without a keyboard, monitor or mouse as it worked fine in dapper, and the firewall rules seem fine to me. ](*,)

---

### Post by TheWizzard on 2006-12-29
can you provide us with a bit more information? what are the exact error messages you receive, etc. also:
- is there a router between the boxes?
- open firestarter and select the tab "events". what do you see here when you try to connect to the server?

---

### Post by Epica on 2006-12-29
I can no longer scan the network at the login screen for XDMCP clients but sometimes using the add host option and typing in the ip works but most often it just shows a black and grey screen with a black cross as a cursor. SSH for the most part works fine, but i can no longer print using IPP as the printer simply prints 
> GIU
V'c-a

firestarter shows no error messages but XNEST and Terminal server client show the following error message

> error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
X connection to :0.0 broken (explicit kill or server shutdown).

any help greatly appreciated :)

---

### Post by TheWizzard on 2006-12-29
ok, to be sure it is not a firestarter problem, open firestarter and click "stop firewall". now try again.
if the problem persists, take a look at this tread: 
[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

---

