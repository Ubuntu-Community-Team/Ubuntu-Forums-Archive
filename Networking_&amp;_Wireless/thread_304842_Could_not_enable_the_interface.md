---
title: "Could not enable the interface"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by sunspots on 2006-11-22
Set up:
- Ubuntu Dapper Drake 6.10
- Belkin F5D6060 wireless PCMCIA card
- Linksys wireless router WRT54GX

About a month ago I got my wireless card working following a thread on one of the forums. Everything has been working well until about a week ago.

I found that the mouse response and any response on the session would take an eternity to respond. Sometimes I could see that the reception has gone, even though I have not moved from the room. But most time, the reception signal shows orange and the computer icon will have a little x in the bottom right hand corner.

Clicking on the icon to get the connection properties and will show status as INACTIVE. However, when I go to the configuration screen, ETH1 will show as being ACTIVE.

I would then DEACTIVATE the  wireless device. I then attempt to ACTIVATE the wireless device and will then get the message:

    COULD NOT ENABLE THE INTERFACE ETH1

     CHECK THAT THE SETTINGS ARE CORRECT FOR THIS NETWORK AND THAT THE COMPUTER IS CORRECTLY CONNECTED TO IT.

But nothing has changed.

I will then reboot the laptop and when I finally log in I find that the device is DEACTIVE. I go back into the configuring the properties and click on the ACTIVATE button. Connection is then restored and I can surf the web and my network, till the next time it happens.

It also runs into the above problem if the laptop is left idle for a period of time.

I checked the forum for answers and the internet, but even though the message may appear the problem is differnt to mine.

Further to the above information (sorry just remembered). I uninstalled the drivers from NDISWRAPPER and tried to re-instal after a reboot. But no change.

Any pointers would be appreciated.
Thanks for listening (well reading).

---

### Post by TMOL on 2006-11-22
I'm getting worse, my computer recognises my wireless card, and can do internet when I plug it into my home hub, but it doesn't find my woreless network, i know it's turned on.

---

