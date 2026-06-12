---
title: "peer-peer with windows&amp;linux machines"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by dbasberg on 2007-12-20
I am a newbie in Linux.  I have a home network with cable modem.  I have peer-peer with the windows machines.  Now I have a 7.10 installation on one machine and wish to make it a local server.  What direction should I go? NFS only works for linux only networks??  What can do peer level or server/workstation networking in a mixed windows linux environments.  I am willing to study any reference material you point out on the internet.  I have some experience with windows networks (LAN admin with NT - not a very knowledgable one though.

TIA
Doug

---

### Post by Penquite on 2007-12-20
Doug,

If all you need is file sharing services and you are using the desktop version rather than server version, then System > Administration > Shared Folders gives you the option of sharing folders using either NFS or SMB (aka SaMBa). Choosing the SMB option will allow you to share files with a windows network.

If you want your linux box to be a server with more network services, such as logon validation, etc.... then you will probably need the server version which is probably not for the newbie as it is generally command line only.

I hope this helps.

Cheers

Matt

---

### Post by dbasberg on 2007-12-20
That is precisely what I needed to know.
Thanks for the sharing of your expertise and rapid reply.

Doug

---

### Post by jonandrews on 2007-12-22
Have a look at my step-by-step XP /Ubuntu networking guide...

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

