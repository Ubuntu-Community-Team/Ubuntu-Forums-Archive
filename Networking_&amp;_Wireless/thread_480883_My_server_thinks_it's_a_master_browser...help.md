---
title: "My server thinks it's a master browser...help"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Cr0n_J0b on 2007-06-21
I'm getting tons of errors on my XP system saying that my UBUNTU server is claining to be the master browser...but it's not...

The master browser has received a server announcement from the computer UBUNTU-VENICE that believes that it is the master browser for the domain on transport NetBT_Tcpip_{D3DB7E44-4FDA-. The master browser is stopping or an election is being forced.

For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/events.asp](http://go.microsoft.com/fwlink/events.asp).

now I turned off the master browser settings in Samba...so what is up here?

thanks

---

### Post by Mr. C. on 2007-06-21
There is a built in priority mechanism in browser elections.  A server will take priority over a workstation; samba acts as a server (i.e. Windows NT server).  There is also local master, preferred master, and os level.

See: 

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#dmbexample](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#dmbexample)

MrC

---

