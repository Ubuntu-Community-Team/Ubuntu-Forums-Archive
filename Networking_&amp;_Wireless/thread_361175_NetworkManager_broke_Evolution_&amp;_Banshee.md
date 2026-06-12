---
title: "NetworkManager broke Evolution &amp; Banshee"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by watsbe on 2007-02-14
I have a plain old computer with a plain old wired connection to a plain old network.
Feisty has installed NetworkManager to tell me about wireless connections I don't have.
Banshee sees NetworkManager, and decides no-one in their right mind would install NetworkManager if they didn't have a wireless connection, assumes I have no current connection and will not look up song titles.
Evolution see NetworkManger installed and follows the same logic.  When I try to connect it puts me off-line so I have to manually go on-line again to see my mail  Haven't had this sort of nonsense since Lotus Notes 4 late last century.
Is there a way to get rid of NetworkManager without breaking the standard desktop package?  Alternately, is there a way to identify the call to NetworkManager and fake the correct response?
Or anything else?

Oh, and daemon.log contains: 
Feb 14 18:40:14 localhost NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
Feisty: 2.6.20-6-386 #2 Wed Jan 31 20:48:57 UTC 2007 i686 GNU/Linux

---

### Post by watsbe on 2007-02-20
I sort of fixed the problem by deleting the pertinent bits from /et/network/interfaces.  This means I lose my static IP so I have to have a look through all other settings and other boxes around the house with the IP set.

---

### Post by dlbolton on 2007-03-07
I have this same issue.  Except in my case it just puts Evolution into offline mode (which of course is now the default - isn't that special?).  I only have to choose "Online" from the file menu, then the send/receive button becomes active and I can get my mail from the server.

I found that I could get banshee to behave normally by killing the NetworkManager related processes. Of couse I will have to do this every time I restart my computer unless I can find a way to either get my network card to work with NetworkManager or remove (or break) NetworkManager.

Dave

---

