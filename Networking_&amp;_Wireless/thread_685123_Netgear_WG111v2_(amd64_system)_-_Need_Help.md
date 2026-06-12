---
title: "Netgear WG111v2 (amd64 system) - Need Help"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Kawayanan on 2008-02-01
I have a netgear wg111v2.  it is a rtl8187 based USB adapter.  I got it because I needed a USB wireless card and it is [listed on supported cards page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") as working out of the box.  I have been trying for a week and a half to get this to work and haven't yet gotten anywhere.

When trying to run it "out of the box" (I assume with the open source driver), it only seems to work on boot about 1/2 the time.  When it does, it only works for a minute or two before dying.  I [posted the errors in the logs]("http://ubuntuforums.org/showthread.php?t=683356"), but never got any suggestions.  I am not sure if the open source driver problems I had were from using a 64 bit system or something else.   

Not having any other ideas, I decided to try out ndiswrapper with the windows drivers (people appear to have gotten that to work).  The problem there is that I have an amd64 system.  As far as I can tell. the people that have gotten the ndiswrapper to work are on 32 bit systems.  The ndiswrapper site says that you should be able to use ndiswrapper on 64 bit systems, but you need the 64 bit windows driver.  I have read all the HOWTO's and threads I can and have tried 6 different 64 bit drivers (4 from netgear, one from Realtek, and one someone posted here).  So foar I haven't been able to get any to work.  Some claim they are not 64 bit drivers (though they are), some give errors on trying to load, and some just seem to quietly not work.

Has anyone been able to get any 64 bit drivers working through ndiswrapper?  Or maybe someone has suggestions on getting the open source drivers working?  I'm willing to try just about anything at this point, and can post any outputs or logs someone might want to see.

Kawayanan

---

### Post by Hightide on 2008-02-02
Hi Kawayanan

Kevdog's wireless tutorial refers to rtl8187 ships being blacklisted due to a known bug. see

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

hope this helps

regards

:)

---

### Post by Kawayanan on 2008-02-02
> **Hightide said:**
> Hi Kawayanan

Kevdog's wireless tutorial refers to rtl8187 ships being blacklisted due to a known bug. see

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

hope this helps

regards

:)

Thanks for the reply.  I read the thread and will give it a try when I get home.  Its strange that I can connect sometimes after a reboot but loose the connection after a couple minutes.  That is with no extra "x" at the end of the essid.  I'll definitally give it a shot though and post what I find.

Kawayanan

---

