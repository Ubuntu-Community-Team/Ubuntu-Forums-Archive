---
title: "Ndiswrapper for D-Link 510G Rev. B not working"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by dahli.llama on 2005-10-14
In Hoary I had my wireless internet working perfectly.  Using Ndiswrapper and the drivers on the install disk for my D-Link 510G card I was able to get everything working.

In Breezy, though, I am having troubles.  I had to download GCC 3.4 to compiler ndiswrapper 1.2 and once that was successfully installed, I try to install my card's driver.  When I do a ndiswrapper -l to see if it installed, I get an error telling my that my driver isn't correct.  I know it is, because it works perfectly n Hoary.

Also, in my Network Config menu, wlan0 is not listed as a network source.

Is there anything I'm missing?  Are there native drivers for this card available?  Any help would be greatly appreciated.

Thank you.

---

### Post by Loop0nBlue on 2005-10-14
Well, I also had a problem with ndiswrapper (with a broadcom 64bit driver). I just found out that the driver permissions changed during breezy update. Just look if it isn't the same for you ; if that's the case, just chmod it, and everything should work fine.

---

### Post by dahli.llama on 2005-10-14
Which permissions?  The permissions on the file couldn't have changed since I am getting them off a CD.

I think I may have found native drivers, but I still need to try it when I get home.

---

