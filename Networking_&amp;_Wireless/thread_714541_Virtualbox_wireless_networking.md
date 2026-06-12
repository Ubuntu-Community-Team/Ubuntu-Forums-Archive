---
title: "Virtualbox wireless networking"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by psilo on 2008-03-03
I'm trying to get Windows file sharing working on an XP guest in Virtualbox.  The host is a laptop running gusty with a wireless network connection.  I followed [**_[COLOR="Blue"]these[/COLOR]_**]("http://www.scottro.net/vboxbridge.html") instructions to set up the bridge for host interface networking.

    The XP guest seems to connect to the network and I can get out to the internet.  When I try to browse the workgroup I can see the other machines on my network but I get a 'network path not found' error when I try to open any of them.  I can browse the shares on a machine if I enter it's ip address in the Run dialog.

    From another machine I can see the XP guest in the workgroup but I get the same error when I click on it.  I can access the share using the ip address.

    I'm not running a WINS server but that doesn't seem to stop the other Windows boxes from browsing each other's shares.  Any ideas?

-john

---

### Post by psilo on 2008-03-03
One more thing, I also can't see any of my other machines shared iTunes libraries and none of the other machines can see the one on the XP guest.  This was one of the main reasons for setting up host interface networking in the 1st place.

---

### Post by psilo on 2008-03-04
*bump*

---

