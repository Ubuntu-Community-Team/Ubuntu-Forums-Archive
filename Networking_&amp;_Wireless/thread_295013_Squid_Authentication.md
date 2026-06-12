---
title: "Squid Authentication"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by mollmann on 2006-11-07
Hello,
I'm using Ubuntu 6.06 LTS and Samba 3 with squid. Winbind is authenticating correctly against the 2000 Active Directory. When a user that's logged onto the domain opens an IE 6.0 session, a box still pops up asking for the user name and password. 

If the user enters the correct information then their ID is recorded in the Squid logs. But if the user closes the window then they can't access squid’s cache.

According to squids "How-to's" the password box shouldn't pop up. I've checked the box in Tools > Internet Options, Advanced, Enable Integrated Windows Authentication in IE, but that doesn't fix the problem. 

This has me stumped; can someone please point me in the right direction?

Thank,
Mark Ollmann

---

### Post by xyrer on 2007-03-21
Hi, i'm looking to replicate the same problem you have, except i need it that way, but i'm not sure if that's exactly how, I need every user to type their username and password from a popup or whatever and keep the user authenticated as long as a window is open, then when the users closes that "authentication window" the navigation stops.
Wingate does that by asking telnet authentication first but I want squid to do it.

I appreciate any help, thanks.

---

