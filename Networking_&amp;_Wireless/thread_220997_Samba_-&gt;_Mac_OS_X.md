---
title: "Samba -&gt; Mac OS X"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by vfxdude2 on 2006-07-22
Ok, I know there are a lot of samba posts... I'll read through them all eventually. :-)

BUT... I'm having a problem I haven't seen mentioned yet.

I'm using the default smb.conf as installed by the "Sharing" control panel in Gnome with ONE modification:  I have "security = user"

When I try to connect from Mac OS X, there are two problems:
1) If I enter my Ubuntu username and password, it won't authenticate
2) If I REMOVE the username and password completely, it WILL authenticate

The problem with (2):  You don't need a password to to access the Ubuntu machine!

That's not good!

Anyone know how to fix this?

Oh, I'm using Dapper and Mac OS X 10.4.7

Thanks!
-vfxdude

---

### Post by vfxdude2 on 2006-07-22
Oh... one other useful piece of information.

I can also access the samba volume from Ubuntu (via Nautilus) with no password.

-vfxdude

---

### Post by gleem on 2006-11-05
I too have the same problem.. in terms of security risk.

blank username and password works great... but with user name.. not?

eek.. I hope their is a fix..


anyone?

---

### Post by dmizer on 2006-11-06
use the link in my sig to set up a samba server.  it's the easiest and most well written howto (it's not my own howto, so i'm not just playing ego trip here).

---

