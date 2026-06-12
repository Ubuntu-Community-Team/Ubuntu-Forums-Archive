---
title: "Networking with Windows Problem"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by petriomelony on 2007-01-11
hey everyone,

i'm having a problem... when i go to places -> network, a Windows Network shows up, but accessing it shows nothing.  i've set up Samba (was i supposed to?) according to one of the guides, but i'm not sure what the matter is.  Any tips? thanks!

---

### Post by jd65pl on 2007-01-11
Have you set up filesharing on the windows computer would will need to do that to share files from the windows computer.
Samba is more orientated towards sharing files from your linux box there are pages on the wiki which are helpful in terms of samba.

---

### Post by FLPCGuy on 2007-01-11
> **petriomelony said:**
> hey everyone,

i'm having a problem... when i go to places -> network, a Windows Network shows up, but accessing it shows nothing.  i've set up Samba (was i supposed to?) according to one of the guides, but i'm not sure what the matter is.  Any tips? thanks!

Assuming you have another machine running Windows server service on the same network segment, if it is XP SP2 or has a firewall, you will need to open up TCP/UDP ports 137 for the NetBIOS Name Service.  Also, you should try restarting your Windows box after you have shared a folder or printer since it generally only advertises it's shares on startup unless polled.  

You might want to check your IPTABLES on your Linux machine to be sure it accepts input on the same port from the local network but be sure your cable modem/router drops port 137 both to or from the Internet. Firewalls are the most likely reason you won't see your Windows PC on your local network, but even without firewalls this broadcast service is slow and takes some patience to use.

---

