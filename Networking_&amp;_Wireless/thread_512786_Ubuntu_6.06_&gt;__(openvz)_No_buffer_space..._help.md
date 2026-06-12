---
title: "Ubuntu 6.06 &gt;  (openvz) No buffer space... help."
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by wastedfluid on 2007-07-29
Okay guys.

Machine is running Fedeora Core 5.. acting a VPS Server, running openvz.

Ubuntu 6.06 is being used.. 

I get LOTS of errors off the VPS.

I'm thinking this is an OS problem, because Ubuntu is hosting an unreal ircd server..  and i also vps'd freebsd, and it's not having this networking issue hosting an ircd server, as well.

After about 100 client connections, I can't ssh into the box, or out of the box.  I get
" No buffer space available"'' 

Sometimes, if you ssh into the box, you get "Connection timed out after handshake" - or something similar to this.

I can't ping the box / out of the box, and nothing works - networking wise.

Off the top of my head, ulimit is set to 1024.. I jacked it up to 65000, but it requires a reboot to make 65,000 go into effect.. and I don't have 1000 in use anyway.

Can anyone help me here?  What more info would you need?  Thanks.

---

