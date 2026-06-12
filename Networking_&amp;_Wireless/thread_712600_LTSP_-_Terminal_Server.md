---
title: "LTSP - Terminal Server"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by IQRules on 2008-03-01
I got myself a bit headache here.
I bought a XPe (Windows XP embedded device). I booted it up, it requires user name and password first. Currently I do not have Windows (Terminal) servers in my network.
Looks to me, this little device tries to authenticate FIRST. So the login fails.

My question is,
Could I use Linux Terminal Server instead of Windows 2003 (Terminal) server?
Is it Windows 2003 server a Terminal Server, I really need for this device?

Any Windows Emulation just like Samba which is available on Linux for this?

---

### Post by Aearenda on 2008-03-01
A Linux terminal server uses a completely different protocol to talk to the terminals from Windows, so LTSP won't solve your problem as presented. 

I am a bit confused about what username and password it is asking for - normal Windows terminals don't ask for a user and password until they have connected to the terminal server. Can you tell us what this device is (manufacturer, model) and what you intend to use it for?

---

