---
title: "Winscp - Can't login to Dapper"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by bayvista on 2006-09-26
I have just upgraded to Dapper. When I start Winscp on my Windows desktop and try to login to Dapper, I get a message 'Network error. Connection refused'. This is strange as I can connect using Windows and access shares on Dapper OK. Windows accepts my userid and password. Winscp doesn't.

I've also noticed that I can't ping anything from Dapper and I can't ping Dapper from Windows. I have a LAN and a router for Internet access.

Winscp was working fine before I upgraded.

This is purely a connect problem. I can transfer files both ways using Explorer and Nautilus.

---

### Post by kidders on 2006-09-26
Hi there,

Something seems a bit funny, in that not being able to ping *anything* usually means you don't have a properly configured network connection. This doesn't quite tally with the idea that you can access your Ubuntu box from elsewhere.

Anyhow "Connection refused" means your Ubuntu box isn't accepting connections on the port your are trying to use. Naturally, to use the SSH protocol, you need to be running an SSH server. If you *are* running one, then tell your firewall :-)

I hope that helps.

---

