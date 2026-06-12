---
title: "Looking for advice on how to fix Samba PDC security holes"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by HeyPig on 2013-11-04
I am trying to patch up some security holes left by our former IT guy.


Basics of the current network:
3 servers
	File Server (samba)
	PDC (samba, LDAP) also houses peoples personal files 
	Email (Zimbra)


The problem is, the file server only has one user, lets call it "derpy", and all the PC's (20ish) talk to the PDC, get fed a plain text .bat on login, and that .bat, with "net use" gives them their network paths in windows explorer.


This makes it so that I cant actually track what users are logged into the file server, everyone shows up as "derpy"


What would you guys do in this situation?


Gotcha's:
	All network drives must remain pathed to the old locations with the correct drive letters

any help would be greatly appreciated! Thanks!

---

### Post by HeyPig on 2013-11-06
Bump :)

---

