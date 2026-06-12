---
title: "Sierra Aircard 860 on Rogers"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Skaught11 on 2008-11-10
I have been trying to get my AC860 to work in 8.10.  I have only had it working in windows before but when I took windows off this computer and upgraded to 8.10 I lost my air card.

I have done my homework and have it installed and accepting AT commands.  I can even connect to the cellular carrier.  It is when I try to get ppp working that things fail.

Here is a copy of my log:
Nov  9 22:31:13 skaught-laptop pppd[32347]: pppd 2.4.4 started by root, uid 0
Nov  9 22:31:13 skaught-laptop pppd[32347]: Using interface ppp0
Nov  9 22:31:13 skaught-laptop pppd[32347]: Connect: ppp0 <--> /dev/ttyS0
Nov  9 22:31:13 skaught-laptop pppd[32347]: CHAP authentication succeeded
Nov  9 22:31:13 skaught-laptop pppd[32347]: CHAP authentication succeeded
Nov  9 22:31:13 skaught-laptop pppd[32347]: Modem hangup
Nov  9 22:31:13 skaught-laptop pppd[32347]: Connection terminated.
Nov  9 22:31:14 skaught-laptop pppd[32347]: Exit.

I am using the new connection manager and having a great deal of difficulty even to get it to save my settings.  It only gives me two choices in Canada, Fido to Rogers AT&T.  Rogers split from AT&T some time ago which leads me to think that the settings Ubuntu is using may be way out of date.

According to Rogers the username and password should be blank but the connection manager refuses to accept a blank entry in the password field.  It simply fills it in with it's own data after I close the window.

Other docs also suggest that Rogers only supports PAP but if I select that, the connection manager thinks otherwise and deletes any changes I make and uses CHAP anyway.

Is there a config file or some other way to get this working?

It would really suck to have to go back to windows over something so silly.

---

