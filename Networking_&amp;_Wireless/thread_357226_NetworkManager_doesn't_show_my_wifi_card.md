---
title: "NetworkManager doesn't show my wifi card"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by thoughts on 2007-02-09
I just installed Edgy on my laptop.  I tried using the System -> Admin -> Networking dialog to connect to my wireless network, but couldn't get it to work (wouldn't connect when I manually entered the SSID and my WPA password; wouldn't scan for open networks).  Eventually I read about NetworkManager, so I installed that.

I now have the NetworkManager icon in my notification area on the taskbar.  But when I click on it, the only item in the list is "Wired Network" (which is grayed out because the cable is disconnected).

But when I run "iwlist scan" in a terminal, it shows all the wifi networks in my area, so the wireless card is definitely working.

Why doesn't NetworkManager pick it up?

My wifi card is a built-in Intel 2200BG.

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by spd106 on 2007-02-09
Have a look at this page in the wiki. [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by thoughts on 2007-02-09
Thanks!  That link had the solution.  I had to go into System -> Admin -> Networking and disable (uncheck) my wifi connection there (and then reboot) so that NetworkManager could pick up the wifi card itself.  Now the NetworkManager icon shows all the wireless networks near me.  Now to try and connect to one of them...

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

