---
title: "Wireless trouble on AA1."
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by DrDoctor on 2008-11-11
I got a weird problem with the wireless/network manager, I'm quite new to Ubuntu, and linux in general, so this might be an easy fix that I'm just too ignorant to find. I've spent about 4 hours searching the web and tried to find a solution, but been unable to. Hopefully a good samaritan will lend a newb a hand.

The scenario:
I bought a Acer Aspire One yesterday, installed Ubuntu 8.10, and set it up to suit my needs, updated etc, on a wired connection. During this time i got a notification that it detected the neighbours wireless networks.

I get home today, try to connect to the WiFi, and this is where the problem occurs. When i click the network manager it only shows the option of wired networks, grayed out seeing how i haven't got a wired connection, and VPN, which i installed for use on campus. It does not show the Wireless option whatsoever. However, if I go to the Edit Connections, there is a Wireless tab. When I check the Hardware Drivers tab under System/Administration it shows i have a wireless driver installed (the default one, if that changes anything).

Normally I'd just try to get a hold of a diffrent driver, but I will not have access to a wired connection on my laptop again for some time, so I can not download anything.

I'm hoping that there's some kind of solution that just involves re-enabeling, or configurating what's already on my computer, and if that's not the case, a way to fix the default drivers when I get back to my wired connection.

---

### Post by Aearenda on 2008-11-11
Take a look through [http://ubuntuforums.org/showthread.php?t=894](http://ubuntuforums.org/showthread.php?t=894) and near the end of [https://help.ubuntu.com/community/AspireOne#Wireless%20Broken%20in%20Intrepid%20RC;%20how%20to%20install%20/home%20to%20an%20SD%20card](https://help.ubuntu.com/community/AspireOne#Wireless%20Broken%20in%20Intrepid%20RC;%20how%20to%20install%20/home%20to%20an%20SD%20card) - I think you need to get the ath5k driver.

---

### Post by DrDoctor on 2008-11-11
If that's the way to go then i guess I'll try that, was sort of hoping I would be able to get the wifi going before coming back on a wired connection, and since the WiFi worked yesterday, I thought it might be something as simple as me messing something up as i went about waving my ignorance all over the system yesterday,

Anyhoo, thank you for your help, at least I know what to do when I get back on the wired connection.

EDIT: 
Managed to get back on a wired net a bit earlier than expected, and now everything works with the ath5k driver. Again, thanks for the help.

---

