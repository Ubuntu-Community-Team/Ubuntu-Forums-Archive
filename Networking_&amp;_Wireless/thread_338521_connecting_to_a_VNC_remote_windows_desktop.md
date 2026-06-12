---
title: "connecting to a VNC remote windows desktop"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by xpan on 2007-01-14
Hi,

I would like to know if it is possible to remotely connect to a windows 2003 server which runs UltraVNC ([http://ultravnc.sourceforge.net/)](http://ultravnc.sourceforge.net/)).

If yes, which program(s) do you suggest?

thanks,
Chris

PS: I am using Edgy Eft.

---

### Post by bernied on 2007-01-14
Yes, use vncviewer. Should be easy enough to find in the repositories.

Depending on how remote your server is, you might consider securing the connection. Vnc on it's own is not considered very secure (I believe). The solution is to tunnel the vnc session inside an ssh session. The server would need to be running an ssh server, or another server on the same network would need to be running an ssh server.

Where are the two machines in relation to one another? Are there routers, firewalls, the big wide world, etc in between?

---

### Post by xpan on 2007-01-15
Thanks for the answer. I could open the windows desktop inside my Ubuntu desktop very easily. I don't use any firewalls or ssh "wrappers". The windows server is not mine. I suppose the administrator of the lab has taken care of those details. 

I just connect on that machine. 

What do you mean when you say: "Vnc on it's own is not considered very secure"?

---

### Post by bernied on 2007-01-15
> What do you mean when you say: "Vnc on it's own is not considered very secure"?
Well, I'm going to be vague, because this is just a vague memory, but this means that it might be possible for someone in between the viewer and the server to intercept, and possibly take charge of the vnc session. If you are doing this in a local network setting, say between two machines at work, then it is probably not a concern, unless you think that there are malicious (and a bit clever) folk about. But if you are doing this across the internet, say from work to home, then you might consider making it more secure. 

If the server is not yours, and the administrator is happy with the way you are connecting, then worry no more.

---

### Post by Gladier on 2007-01-15
not to mention that all passwords/mouse movements/keystrokes are sent in plain text

the picture you are recieving isnt that hard to decode to jpegs either - so there is basically no real "security"

which is why bernied says it should be sent through a secure tunnel - so noone else can decrypt it

---

### Post by nyvalbanat on 2007-01-16
> **xpan said:**
> Hi,

I would like to know if it is possible to remotely connect to a windows 2003 server which runs UltraVNC ([http://ultravnc.sourceforge.net/)](http://ultravnc.sourceforge.net/)).

If yes, which program(s) do you suggest?

thanks,
Chris

PS: I am using Edgy Eft.


Have you tried using rdesktop instead? It connects directly to your terminal server. I use it all the time.

-Val

---

